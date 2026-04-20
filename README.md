# DZ_OOP.Na_1
// Калькулятор двух числе.cpp : Этот файл содержит функцию "main". Здесь начинается и заканчивается выполнение программы.
//

#include <iostream>
#include <string>
#include <Windows.h>
#include <fstream>

using namespace std;

class Figure {
	protected:
		int sides_count;
		string name;

	public:
		// Конструктор по умолчанию (для фигуры)
		Figure(int sides = 0) : sides_count(sides), name("Фигура") {}

		virtual ~Figure() {}

		int get_sides_count() const {
			return sides_count;
		}

		string get_name() const {
			return name;
		}
};

// Треугольник
class Triangle : public Figure {
public:
	Triangle() : Figure(3) {
		name = "Треугольник";
	}
};

//Четырёхугольник
class Quadrangle : public Figure {
	public:
		Quadrangle() : Figure(4) {
			name = "Четырёхугольник";
		}
};

int main()
{
	setlocale(LC_ALL, "Russian");
	SetConsoleCP(1251);
	SetConsoleOutputCP(1251);

	int sides;
	cout << "Количество сторон: " << endl;
	cin >> sides;

	Figure* figure = nullptr;

	if (sides == 3) 
	{
		figure = new Triangle();
	}
	else if (sides == 4)
	{
		figure = new Quadrangle();
	} else {
		figure = new Figure(sides);
	}

	cout << figure->get_name() << ": "
		<< figure->get_sides_count() << endl;

	delete figure; //удаление

	return 0;
}

