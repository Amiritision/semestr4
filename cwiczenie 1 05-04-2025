using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Paczka;
using Paczka.FactoryClasses;
using Paczka.Intefaces;
using Paczka.Packages;
using Paczka.Intefaces;

//packagemanager za pomoca singletona dzieki temu w calym programie bedzie jedna instancja klasy packetmanager;
var packageManager = PackageManager.Instance;

var order1 = new List<IFactoryPackage>
{
    new FactoryBigPackage(),
    new FactoryMidPackage(),
    new FactorySmallPackage(),
};

var order2 = new List<IFactoryPackage>
{
    new FactorySmallPackage(),
    new FactoryMidPackage(),
    new FactoryBigPackage(),

};

var order3 = new List<IFactoryPackage>
{
    new FactoryBigPackage(),
    new FactoryMidPackage(),
    new FactorySmallPackage(),

};
// wyswietlanie i przygotowanie paczek dla kazdego z zamówień;
Console.WriteLine("Zamówienie 1");
packageManager.PrepareOrder(order1);

Console.WriteLine();
Console.WriteLine("Zamówienie 2");
packageManager.PrepareOrder(order2);

Console.WriteLine();
Console.WriteLine("Zamówienie 3");
packageManager.PrepareOrder(order3);


Console.ReadKey();


namespace Paczka
{
    class PackageManager
    {
        private static PackageManager _instance = default!;
        public static PackageManager Instance
        {
            get
            {
                if (_instance == null) { _instance = new PackageManager(); }
                return _instance;
            }
        }
        private PackageManager() { }

        public void PrepareOrder(List<IFactoryPackage> packagesFactory)
        {
            foreach (var packageFactory in packagesFactory)
            {
                var package = packageFactory.CreatePackage();
                package.PreparePackage();
            }
        }
    }
}

//fabryka duzej paczki
namespace Paczka.FactoryClasses
{
    internal class FactoryBigPackage : IFactoryPackage
    {
        public IPackage CreatePackage() => new BigPackage();
    }
}
//fabryka sredniej paczki
namespace Paczka.FactoryClasses
{
    class FactoryMidPackage : IFactoryPackage
    {
        public IPackage CreatePackage() => new MediumPackage();
    }
}
//definicja fabryki malej paczki
namespace Paczka.FactoryClasses
{
    class FactorySmallPackage : IFactoryPackage
    {
        public IPackage CreatePackage() => new SmallPackage();
    }
}
//// klasa bigpackage - reprezentuje duza paczke
namespace Paczka.Packages
{
    internal class BigPackage : IPackage
    {
        public void PreparePackage()
        {
            Console.WriteLine("Prygotowano duża paczkę");
        }
    }
}

//definicja klasy smallpackage - reprezentuje mala paczke
namespace Paczka.Packages
{
    public class SmallPackage : IPackage
    {
        public void PreparePackage()
        {
            Console.WriteLine("Przygotowano małą paczkę");
        }
    }
}

//definicja klasy mediumpackage - reprezentuje srednia paczke
namespace Paczka.Packages
{
    public class MediumPackage : IPackage
    {
        public void PreparePackage()
        {
            Console.WriteLine("Przygotowaną średnią paczkę");
        }
    }
}



//definicja ifactorypackage - fabryka paczek ktora tworzy paczki
namespace Paczka.Intefaces
{
    internal interface IFactoryPackage
    {
        IPackage CreatePackage();
    }
}
//definicja interfejsu ipackage - reprezentuje paczke ktora moze byc przygotowana
namespace Paczka.Intefaces
{
    internal interface IPackage
    {
        public void PreparePackage();
    }
}
