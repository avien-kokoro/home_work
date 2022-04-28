# home_work
my homework!


#include <iostream>

using namespace std;


int i = 1;
int GCD = 1;

int find_GCD(int x, int y);

class Fraction {
public:

	Fraction(int n, int d = 1)
	{
		setFraction(n, d);
	};
	int getNum() const
	{
		int _num;
		_num = num;
		return _num;
	};
	int getDen() const
	{
		int _den;
		_den = den;
		return _den;
	};
	void setFraction(int n, int d)
	{
		int i;
		i= find_GCD(n, d);
		n /= i;
		d /= i;
		if (!(n == 0) && (d < 0))
		{
			n = -n;
			d = -d;
		}
		if (n == 0)
		{
			d = 1;
		}
		num = n;//분자
		den = d;//분모
		
	};
	// convert n/d to an irreducible fraction with positive denominator 
private:
	int num;	          // numerator
	int den;		// denominator; positive integer
};


int find_GCD(int x, int y)
{
	if (x < 0)
	{
		x = -x;
	}
	if (y < 0)
	{
		y = -y;
	}
	if (x < y)
	{
		int temp;
		temp = x;
		x = y;
		y = temp;
	}
	if (x % y == 0)
	{
		return y;
	}
	else
	{
		return find_GCD(y, x % y);
	}
}

/*
int find_GCD(int x, int y)
{
	if (x < 0)
	{
		x = -x;
	}
	if (y < 0)
	{
		y = -y;
	}
	int min_num = 1;
	min_num = x;

	if (x > y)
	{
		min_num = y;
	}
	for (int i = 1; min_num >= i; i++)
	{
		if ((x % i == 0) && (y % i == 0))
		{
			GCD = i;
		}
	}
	return GCD;
}*/

Fraction add(Fraction x, Fraction y)
{
	int new_num;
	new_num = x.getNum() * y.getDen() + y.getNum() * x.getDen();
	int new_den;
	new_den = x.getDen() * y.getDen();
	Fraction z1(new_num, new_den);
	return z1;
};

Fraction subtract(Fraction x, Fraction y)
{
	int new_num;
	new_num = x.getNum() * y.getDen() - y.getNum() * x.getDen();
	int new_den;
	new_den = x.getDen() * y.getDen();
	Fraction z2(new_num, new_den);
	return z2;
};

Fraction multiply(Fraction x, Fraction y)
{
	int new_num;
	new_num = x.getNum() * y.getNum();
	int new_den;
	new_den = x.getDen() * y.getDen();
	Fraction z3(new_num, new_den);
	return z3;
};

Fraction divide(Fraction x, Fraction y)
{
	int new_num;
	new_num = x.getNum() * y.getDen();
	int new_den;
	new_den = x.getDen() * y.getNum();
	Fraction z4(new_num, new_den);
	return z4;
};





int main()
{
	cout << "Enter the numerator and denominator of the first fraction: ";
	int x1, y1;
	cin >> x1 >> y1;
	Fraction First_fraction(x1, y1);
	cout << "First fraction: " << First_fraction.getNum() << "/" << First_fraction.getDen() << endl;


	cout << "Enter the numerator and denominator of the second fraction: ";
	int x2, y2;
	cin >> x2 >> y2;
	Fraction Second_fraction(x2, y2);
	cout << "Second fraction: " << Second_fraction.getNum() << "/" << Second_fraction.getDen() << endl;



	cout << "(" << First_fraction.getNum() << "/" << First_fraction.getDen() << ") + (" << Second_fraction.getNum() << "/" << Second_fraction.getDen() << ") = " << add(First_fraction, Second_fraction).getNum() << "/" << add(First_fraction, Second_fraction).getDen() << endl;
	cout << "(" << First_fraction.getNum() << "/" << First_fraction.getDen() << ") - (" << Second_fraction.getNum() << "/" << Second_fraction.getDen() << ") = " << subtract(First_fraction, Second_fraction).getNum() << "/" << subtract(First_fraction, Second_fraction).getDen() << endl;
	cout << "(" << First_fraction.getNum() << "/" << First_fraction.getDen() << ") * (" << Second_fraction.getNum() << "/" << Second_fraction.getDen() << ") = " << multiply(First_fraction, Second_fraction).getNum() << "/" << multiply(First_fraction, Second_fraction).getDen() << endl;
	cout << "(" << First_fraction.getNum() << "/" << First_fraction.getDen() << ") / (" << Second_fraction.getNum() << "/" << Second_fraction.getDen() << ") = " << divide(First_fraction, Second_fraction).getNum() << "/" << divide(First_fraction, Second_fraction).getDen() << endl;


}
