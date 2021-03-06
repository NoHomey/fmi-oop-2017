# Const references

�� ����� �� ����� ����� ��� ���������, ���� � ��� ����������.
��������� �� ����:

    const int NINE = 9;
    int ten = 10;
    const int& ref_9 = NINE;
    const int& ref_10 = ten;
    
�� ����� �� �������� �������� ���� ������ ����������, ���� �� �� ���� ��� ����������.
�� ���������� 4 ���� ���� ���� � �������:

    NINE++;       // ��������� - NINE � ��������� � �� ���� �� �� �������. 
    ref_9++;      // ��������� - ref_9 � const ���������� � �� ����� �� �������� �������� ���� ���. 
    ten++;        // �� - ten e ���������� � ����� �� � ������ ����������.
    ref_10++;     // ��������� - ref_10 � const ���������� � ������� �� ���� ��� ����������,
                  // �� ����� �� �������� �������� ���� ���. 

� ������, �� const ������������ ���� ��� ����� �� ����, ����� �� ������ ���� ��������, ���������� � const:

    Vector3D {
        // ...
        void set_x(double _x) {
            x = _x;
        }
        double get_x() const {
            return x;
        }
    };
    
    int main() {
        Vector3D vec(1,2,3);
        const Vector3D& ref = vec;
        cout << ref.get_x();       // �� - ������ const ����� �� const ����������.
        ref.set_x(4);              // ������ - �� ����� �� �������� �����, ����� �� � ������� � const.
    }

## Const references ��� �������

Const ������������, ����� � ������������ ����������, �� ��������� ���-���� ������ �������� ��������� �� �������, 
�� �� �� �� ������� ������� (������� ��� ���������� � ����� �� ����).

������ ���������� �������, �������� �������� ���� ���������� ����������, ����� �� �������� ���� ���������� � ����� �� ������ ����������
�� ������������ ����� ��� ��������� (��� ������������ � ����� �� ����, ����� �� ������ ����� �� �������� ��).

������ ���������� �������, �������� �������� ���� const ����������, ����� �� �������� ����� ����������, ���� � ��������� �
�� ����� �� ��������� ��������� ����� ��� ��������� (��� ���������� � �� ����, ����� �� ������ ���� const �������� ��).

    int digits_sum(const int& n) {
        int sum = 0;
        while(n > 0) {
            sum += n % 10;
            n /= 10;        // ������ - n �� ���� �� �� �������.
        }
        return sum;
    }
    
����� �� ������� �������� ���������:

    int cube(const int& x) {
        return x * x * x;
    }
    int main() {
        cout << cube(10);     // �� - ������� � (���� ��) ������� �� �������� �� ���� ������...
    }

���������� � ��:

- �������� ���������� ����������, ������ ��������� ���� �� ������� ��������� (� ������ ��� �� �� �������) - ������ �� ����� �� �������� ���������.
- �������� const ����������, ������ ��������� �� ������� ��������� �� ������� ����� - ������ � �� �� �� ������� ���������.
