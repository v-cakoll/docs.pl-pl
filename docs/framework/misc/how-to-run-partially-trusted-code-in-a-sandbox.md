---
title: 'Porady: uruchamianie częściowo zaufanego kodu w bibliotece'
ms.date: 03/30/2017
helpviewer_keywords:
- partially trusted code
- sandboxing
- partial trust
- restricted security environment
- code security, sandboxing
ms.assetid: d1ad722b-5b49-4040-bff3-431b94bb8095
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 05ab0874c980d9e6138ae2bfd720c6d89628613c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a>Porady: uruchamianie częściowo zaufanego kodu w bibliotece
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Sandboxing polega na uruchamianie kodu w środowisku ograniczonych zabezpieczeń, co ogranicza uprawnienia dostępu do kodu. Na przykład jeśli masz zarządzanej biblioteki ze źródła, który całkowicie nie ufasz, nie należy uruchamiać go jako w pełni zaufany. Zamiast tego należy umieszczać kod w izolowanym, która ogranicza uprawnienia do tych, które można spodziewać się muszą (na przykład <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> uprawnień).  
  
 Sandboxing można również używać do testowania kodu, który będzie rozpowszechniania uruchamianego w środowiskach częściowo zaufany.  
  
 <xref:System.AppDomain> Jest efektywnym sposobem zapewnienia piaskownicy zarządzanych aplikacji. Domeny aplikacji, które są używane do uruchamiania częściowo zaufany kod uprawnień, które definiują chronionych zasobów, które są dostępne podczas uruchamiania w tym <xref:System.AppDomain>. Kod uruchamiany w <xref:System.AppDomain> jest powiązany uprawnienia skojarzone z <xref:System.AppDomain> i będzie mógł uzyskać dostępu do określonych zasobów. <xref:System.AppDomain> Obejmuje również <xref:System.Security.Policy.StrongName> tablica, która służy do identyfikowania zestawów, które mają być załadowany jako w pełni zaufany. Dzięki temu twórca <xref:System.AppDomain> można uruchomić nowej domeny piaskownicy, umożliwiający zestawy określonego pomocnika być w pełni zaufany. Inną opcją w przypadku ładowania zestawów jako w pełni zaufany jest umieszczenie ich w pamięci podręcznej GAC; Jednakże, który będzie ładowanie zestawów jako w pełni zaufany we wszystkich domenach aplikacji utworzone na tym komputerze. Lista silnych nazw obsługiwanych na-<xref:System.AppDomain> decyzja, który zapewnia bardziej restrykcyjne określenie.  
  
 Można użyć <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> przeciążenie metody, aby określić uprawnienia ustawione dla aplikacji działających w piaskownicy. To przeciążenie umożliwia określenie dokładnej poziom zabezpieczeń dostępu kodu, który ma. Zestawy, które są ładowane do <xref:System.AppDomain> przy użyciu tego przeciążenia może albo mieć określony tylko zestaw uprawnień lub może być w pełni zaufany. Zestaw otrzymuje pełne zaufanie, gdy jest on w globalnej pamięci podręcznej zestawów lub na liście `fullTrustAssemblies` ( <xref:System.Security.Policy.StrongName>) parametr tablicy. Tylko zestawy wiadomo, że są w pełni zaufany, należy dodać do `fullTrustAssemblies` listy.  
  
 Przeciążenie ma następującą sygnaturą:  
  
```  
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 Parametry <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> przeciążenie metody Określ nazwę <xref:System.AppDomain>, dowód <xref:System.AppDomain>, <xref:System.AppDomainSetup> obiekt, który identyfikuje baza aplikacji piaskownicy, uprawnienia do użycia i silnej nazwy całkowicie zaufanych zestawów.  
  
 Ze względów bezpieczeństwa baza aplikacji określonego w `info` parametr nie może być podstawowy dla hostingu aplikacji aplikacji.  
  
 Dla `grantSet` parametru, możesz określić zestaw uprawnień, jawnie utworzono lub standardowe uprawnienie zestaw utworzony przez <xref:System.Security.SecurityManager.GetStandardSandbox%2A> metody.  
  
 W przeciwieństwie do większości <xref:System.AppDomain> ładuje dowód <xref:System.AppDomain> (przekazywane przez `securityInfo` parametru) nie jest używane do określania zestaw częściowo zaufanych zestawów uprawnień. Zamiast tego niezależnie jest określona przez `grantSet` parametru. Jednak dowody może służyć do innych celów, takich jak określanie zakres magazynu izolowanego.  
  
### <a name="to-run-an-application-in-a-sandbox"></a>Aby uruchomić aplikację w bibliotece  
  
1.  Utwórz zestaw mieć uprawnienia do niezaufanych aplikacji uprawnień. To minimalne uprawnienia można przyznać <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> uprawnienia. Można również przyznać dodatkowe uprawnienia, które zdaniem użytkownika mogą być bezpieczne dla kodzie niezaufanym; na przykład <xref:System.Security.Permissions.IsolatedStorageFilePermission>. Poniższy kod tworzy nowy zestaw uprawnień o tylko <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> uprawnienia.  
  
    ```  
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     Alternatywnie można użyć istniejącego nazwany zestaw uprawnień, takich jak Internet.  
  
    ```  
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <xref:System.Security.SecurityManager.GetStandardSandbox%2A> Metoda zwraca albo `Internet` zestaw uprawnień lub `LocalIntranet` zestaw uprawnień w zależności od strefy na dowód. <xref:System.Security.SecurityManager.GetStandardSandbox%2A> Tworzy uprawnienia dotyczące tożsamości dla niektórych obiektów dowód przekazany jako odwołania.  
  
2.  Podpisz zestaw zawierający klasę hostingu (o nazwie `Sandboxer` w tym przykładzie), który odwołuje się kodzie niezaufanym. Dodaj <xref:System.Security.Policy.StrongName> używany do podpisywania zestawu do <xref:System.Security.Policy.StrongName> tablicę `fullTrustAssemblies` parametr <xref:System.AppDomain.CreateDomain%2A> wywołania. Klasa hostująca musi działać jako w pełni zaufany, aby umożliwić wykonywanie kodu częściowego zaufania lub aktualnych aplikacji częściowego zaufania. Jest to, jak przeczytać <xref:System.Security.Policy.StrongName> zestawu:  
  
    ```  
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     Nie masz zestawy .NET framework, takich jak mscorlib i System.dll mają zostać dodane do listy pełnego zaufania, ponieważ są one załadowany jako w pełni zaufany z globalnej pamięci podręcznej zestawów.  
  
3.  Inicjowanie <xref:System.AppDomainSetup> parametr <xref:System.AppDomain.CreateDomain%2A> metody. Z tym parametrem można kontrolować wiele ustawień nowej <xref:System.AppDomain>. <xref:System.AppDomainSetup.ApplicationBase%2A> Właściwość jest ustawienie ważne i powinien być inny niż <xref:System.AppDomainSetup.ApplicationBase%2A> właściwość <xref:System.AppDomain> hostingu aplikacji. Jeśli <xref:System.AppDomainSetup.ApplicationBase%2A> ustawienia są takie same, aplikacja częściowego zaufania może uzyskać ładowanie (jako w pełni zaufany) wystąpił wyjątek definiuje, w związku z tym wykorzystuje je hostingu aplikacji. Jest to kolejny powód, dlaczego catch (wyjątek) nie jest zalecane. Ustawienie aplikacji base hosta inaczej niż baza aplikacji w trybie piaskownicy aplikacji zmniejsza ryzyko luki w zabezpieczeniach.  
  
    ```  
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4.  Wywołanie <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> przeciążenie metody, aby utworzyć domenę aplikacji przy użyciu parametrów została określona.  
  
     Podpis dla tej metody jest:  
  
    ```  
    public static AppDomain CreateDomain(string friendlyName,   
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,   
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     Informacje dodatkowe:  
  
    -   Jest to tylko przeciążenia <xref:System.AppDomain.CreateDomain%2A> metody pobierającej <xref:System.Security.PermissionSet> jako parametr, a zatem tylko przeciążenia, które pozwala załadować aplikacji w ustawieniu częściowego zaufania.  
  
    -   `evidence` Parametr nie jest używany do obliczania zestawu uprawnień; jest używany do identyfikacji przez inne funkcje programu .NET Framework.  
  
    -   Ustawienie <xref:System.AppDomainSetup.ApplicationBase%2A> właściwość `info` parametr jest wymagany dla tego przeciążenia.  
  
    -   `fullTrustAssemblies` Parametr ma `params` — słowo kluczowe, co oznacza, że nie jest konieczne tworzenie <xref:System.Security.Policy.StrongName> tablicy. Dozwolone jest przekazywanie 0, 1 lub więcej silnych nazw jako parametrów.  
  
    -   Kod, aby utworzyć domenę aplikacji jest:  
  
    ```  
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5.  Ładowanie kod do sandboxing <xref:System.AppDomain> utworzony. Można to zrobić na dwa sposoby:  
  
    -   Wywołanie <xref:System.AppDomain.ExecuteAssembly%2A> metody dla zestawu.  
  
    -   Użyj <xref:System.Activator.CreateInstanceFrom%2A> metodę w celu utworzenia wystąpienia klasy pochodzące z <xref:System.MarshalByRefObject> w nowym <xref:System.AppDomain>.  
  
     Druga metoda jest preferowana, ponieważ ułatwi do przekazania parametrów do nowego <xref:System.AppDomain> wystąpienia. <xref:System.Activator.CreateInstanceFrom%2A> Metoda zapewnia dwie ważne funkcje:  
  
    -   Można użyć bazy kodu, który wskazuje lokalizację, która nie zawiera używanego zestawu.  
  
    -   Możliwość tworzenia w obszarze <xref:System.Security.CodeAccessPermission.Assert%2A> dla pełnego zaufania (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), która umożliwia utworzenie wystąpienia klasy krytyczne. (Dzieje się to za każdym razem z zestawu ma nie oznaczenia przezroczystość i jest załadowany jako w pełni zaufany.) Dlatego należy należy zachować ostrożność utworzyć tylko kod, którym ufasz, że za pomocą tej funkcji i zaleca się utworzenie tylko wystąpienia klas w pełni zaufany w nowej domenie aplikacji.  
  
    ```  
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     Należy pamiętać, aby można było utworzyć wystąpienia klasy w nowej domenie, klasa ma rozszerzenie <xref:System.MarshalByRefObject> — klasa  
  
    ```  
    class Sandboxer:MarshalByRefObject  
    ```  
  
6.  Dekodowanie nowe wystąpienie domeny do odwołania w tej domenie. To odwołanie jest używane do wykonywania kodu niezaufanych.  
  
    ```  
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7.  Wywołanie `ExecuteUntrustedCode` metody w wystąpieniu `Sandboxer` klasy właśnie utworzony.  
  
    ```  
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     To wywołanie jest wykonywany w domenie aplikacji piaskownicy, która ma ograniczone uprawnienia.  
  
    ```  
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
        {  
            //Load the MethodInfo for a method in the new assembly. This might be a method you know, or   
            //you can use Assembly.EntryPoint to get to the entry point in an executable.  
            MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
            try  
            {  
                // Invoke the method.  
                target.Invoke(null, parameters);  
            }  
            catch (Exception ex)  
            {  
            //When information is obtained from a SecurityException extra information is provided if it is   
            //accessed in full-trust.  
                (new PermissionSet(PermissionState.Unrestricted)).Assert();  
                Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
    CodeAccessPermission.RevertAssert();  
                Console.ReadLine();  
            }  
        }  
    ```  
  
     <xref:System.Reflection> Służy do uzyskania dojścia metody w częściowo zaufanym zestawie. Dojście może służyć do wykonywania kodu w bezpieczny sposób z minimalne uprawnienia.  
  
     W poprzednim kodzie <xref:System.Security.PermissionSet.Assert%2A> uprawnienia pełnego zaufania przed wydrukowaniem <xref:System.Security.SecurityException>.  
  
    ```  
    new PermissionSet(PermissionState.Unrestricted)).Assert()  
    ```  
  
     Assert pełnego zaufania jest używany do uzyskania rozszerzonych informacji z <xref:System.Security.SecurityException>. Bez <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.SecurityException.ToString%2A> metody <xref:System.Security.SecurityException> wykryje, że jest częściowo zaufany kod na stosie i ograniczy zwrócone informacje. Może to spowodować problemy z zabezpieczeniami, jeśli kod częściowego zaufania można odczytać informacji, ale ryzyko skuteczność została osłabiona przez nieprzyznanie <xref:System.Security.Permissions.UIPermission>. Assert pełnego zaufania, które powinny być używane rzadko i tylko wtedy, gdy masz pewność, że użytkownik nie zezwalają na kod częściowego zaufania, aby podnieść poziom do pełnego zaufania. Jako zasada nie należy wywoływać kodu, w którym nie ufasz w tej samej funkcji i po wywołaniu assert dla pełnego zaufania. Należy dobrze przywrócić assert po zakończeniu korzystania z niego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera procedura w poprzedniej sekcji. W tym przykładzie projektu o nazwie `Sandboxer` w programie Visual Studio rozwiązanie zawiera również projektu o nazwie `UntrustedCode`, która implementuje klasy `UntrustedClass`. W tym scenariuszu przyjęto został pobrany w zestawie biblioteki zawierający metodę, która powinna zwrócić `true` lub `false` wskazująca, czy liczba podane jest liczbą Fibonacci. Zamiast tego metodę podejmuje próbę odczytania pliku z komputera. Poniższy przykład przedstawia kod niezaufanych.  
  
```  
using System;  
using System.IO;  
namespace UntrustedCode  
{  
    public class UntrustedClass  
    {  
        // Pretend to be a method checking if a number is a Fibonacci  
        // but which actually attempts to read a file.  
        public static bool IsFibonacci(int number)  
        {  
           File.ReadAllText("C:\\Temp\\file.txt");  
           return false;  
        }  
    }  
}  
```  
  
 W poniższym przykładzie przedstawiono `Sandboxer` kodu aplikacji, która wykonuje kodzie niezaufanym.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.IO;  
using System.Security;  
using System.Security.Policy;  
using System.Security.Permissions;  
using System.Reflection;  
using System.Runtime.Remoting;  
  
//The Sandboxer class needs to derive from MarshalByRefObject so that we can create it in another   
// AppDomain and refer to it from the default AppDomain.  
class Sandboxer : MarshalByRefObject  
{  
    const string pathToUntrusted = @"..\..\..\UntrustedCode\bin\Debug";  
    const string untrustedAssembly = "UntrustedCode";  
    const string untrustedClass = "UntrustedCode.UntrustedClass";  
    const string entryPoint = "IsFibonacci";  
    private static Object[] parameters = { 45 };  
    static void Main()  
    {  
        //Setting the AppDomainSetup. It is very important to set the ApplicationBase to a folder   
        //other than the one in which the sandboxer resides.  
        AppDomainSetup adSetup = new AppDomainSetup();  
        adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
  
        //Setting the permissions for the AppDomain. We give the permission to execute and to   
        //read/discover the location where the untrusted code is loaded.  
        PermissionSet permSet = new PermissionSet(PermissionState.None);  
        permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
  
        //We want the sandboxer assembly's strong name, so that we can add it to the full trust list.  
        StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
  
        //Now we have everything we need to create the AppDomain, so let's create it.  
        AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
  
        //Use CreateInstanceFrom to load an instance of the Sandboxer class into the  
        //new AppDomain.   
        ObjectHandle handle = Activator.CreateInstanceFrom(  
            newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
            typeof(Sandboxer).FullName  
            );  
        //Unwrap the new domain instance into a reference in this domain and use it to execute the   
        //untrusted code.  
        Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
        newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    }  
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new Assembly. This might be a method you know, or   
        //you can use Assembly.EntryPoint to get to the main function in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            //Now invoke the method.  
            bool retVal = (bool)target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
            // When we print informations from a SecurityException extra information can be printed if we are   
            //calling it with a full-trust stack.  
            (new PermissionSet(PermissionState.Unrestricted)).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
