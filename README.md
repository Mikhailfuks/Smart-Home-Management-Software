using System;
using System.Collections.Generic;

namespace SmartHome
{
    class Program
    {
        static void Main(string[] args)
        {
            SmartHomeSystem smartHome = new SmartHomeSystem();
            int choice;

            do
            {
                Console.WriteLine("1. Управление освещением");
                Console.WriteLine("2. Управление температурой");
                Console.WriteLine("3. Управление безопасностью");
                Console.WriteLine("0. Выход");
                Console.Write("Выберите опцию: ");
                choice = Convert.ToInt32(Console.ReadLine());

                switch (choice)
                {
                    case 1:
                        ManageLighting(smartHome);
                        break;
                    case 2:
                        ManageTemperature(smartHome);
                        break;
                    case 3:
                        ManageSecurity(smartHome);
                        break;
                    case 0:
                        Console.WriteLine("Выход из программы.");
                        break;
                    default:
                        Console.WriteLine("Неверный выбор. Попробуйте снова.");
                        break;
                }

            } while (choice != 0);
        }

        static void ManageLighting(SmartHomeSystem smartHome)
        {
            Console.Write("Введите состояние освещения (включить/выключить): ");
            string state = Console.ReadLine().ToLower();
            smartHome.SetLighting(state == "включить");
        }

        static void ManageTemperature(SmartHomeSystem smartHome)
        {
            Console.Write("Введите желаемую температуру: ");
            int temperature = Convert.ToInt32(Console.ReadLine());
            smartHome.SetTemperature(temperature);
        }

        static void ManageSecurity(SmartHomeSystem smartHome)
        {
            Console.Write("Введите состояние безопасности (включить/выключить): ");
            string state = Console.ReadLine().ToLower();
            smartHome.SetSecurity(state == "включить");
        }
    }

    public class SmartHomeSystem
    {
        public bool IsLightOn { get; private set; }
        public int Temperature { get; private set; }
        public bool IsSecurityActive { get; private set; }

        public void SetLighting(bool state)
        {
            IsLightOn = state;
            Console.WriteLine($"Освещение теперь {(state ? "включено" : "выключено")}.");
        }

        public void SetTemperature(int temperature)
        {
            Temperature = temperature;
            Console.WriteLine($"Температура установлена на {temperature}°C.");
        }

        public void SetSecurity(bool state)
        {
            IsSecurityActive = state;
            Console.WriteLine($"Система безопасности теперь {(state ? "активна" : "деактивирована")}.");
        }
    }
}
