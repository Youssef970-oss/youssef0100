import math

class Calculator:
    def _init_(self):
        self.history = []
    
    def add(self, a, b):
        result = a + b
        self.history.append(f"{a} + {b} = {result}")
        return result
    
    def subtract(self, a, b):
        result = a - b
        self.history.append(f"{a} - {b} = {result}")
        return result
    
    def multiply(self, a, b):
        result = a * b
        self.history.append(f"{a} * {b} = {result}")
        return result
    
    def divide(self, a, b):
        if b == 0:
            raise ValueError("لا يمكن القسمة على صفر!")
        result = a / b
        self.history.append(f"{a} / {b} = {result}")
        return result
    
    def power(self, a, b):
        result = a ** b
        self.history.append(f"{a} ^ {b} = {result}")
        return result
    
    def square_root(self, a):
        if a < 0:
            raise ValueError("لا يمكن حساب الجذر لعدد سالب!")
        result = math.sqrt(a)
        self.history.append(f"√{a} = {result}")
        return result
    
    def show_history(self):
        print("\nسجل العمليات:")
        for operation in self.history[-5:]:  # عرض آخر 5 عمليات
            print(operation)
    
    def run(self):
        print("""
        ┌───────────────────────────┐
        │       آلة حاسبة متكاملة      │
        └───────────────────────────┘
        العمليات المتاحة:
        1. الجمع (+)
        2. الطرح (-)
        3. الضرب (*)
        4. القسمة (/)
        5. الأس (^)
        6. الجذر التربيعي (√)
        7. عرض سجل العمليات
        8. الخروج
        """)
        
        while True:
            try:
                choice = input("اختر العملية (1-8): ")
                
                if choice == '8':
                    print("شكراً لاستخدام الآلة الحاسبة. إلى اللقاء!")
                    break
                
                elif choice == '7':
                    self.show_history()
                    continue
                
                elif choice == '6':
                    num = float(input("ادخل الرقم: "))
                    print(f"النتيجة: √{num} = {self.square_root(num)}")
                
                elif choice in ['1', '2', '3', '4', '5']:
                    num1 = float(input("ادخل الرقم الأول: "))
                    num2 = float(input("ادخل الرقم الثاني: "))
                    
                    if choice == '1':
                        print(f"النتيجة: {num1} + {num2} = {self.add(num1, num2)}")
                    elif choice == '2':
                        print(f"النتيجة: {num1} - {num2} = {self.subtract(num1, num2)}")
                    elif choice == '3':
                        print(f"النتيجة: {num1} * {num2} = {self.multiply(num1, num2)}")
                    elif choice == '4':
                        print(f"النتيجة: {num1} / {num2} = {self.divide(num1, num2)}")
                    elif choice == '5':
                        print(f"النتيجة: {num1} ^ {num2} = {self.power(num1, num2)}")
                
                else:
                    print("اختيار غير صالح. الرجاء المحاولة مرة أخرى.")
            
            except ValueError as e:
                print(f"خطأ: {e}")
            except Exception as e:
                print(f"حدث خطأ غير متوقع: {e}")

# تشغيل الآلة الحاسبة
if _name_ == "_main_":
    calc = Calculator()
    calc.run()
