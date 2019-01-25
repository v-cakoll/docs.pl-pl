---
title: 'Instrukcje: Uruchamianie częściowo zaufanego kodu w piaskownicy'
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
ms.openlocfilehash: b33750e5792dcc83e261bc9bb8d1c5dbe35808aa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627229"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a>Instrukcje: Uruchamianie częściowo zaufanego kodu w piaskownicy
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Tryb piaskownicy jest rozwiązaniem polegającym na uruchamianie kodu w środowisku ograniczonych zabezpieczeń ogranicza uprawnienia udzielone do kodu. Na przykład jeśli masz zarządzanej biblioteki ze źródła, którym ufasz całkowicie, nie należy uruchamiać go jako w pełni zaufany. Zamiast tego należy umieszczać kodu w piaskownicy, która ogranicza uprawnienia do tych, które mogą potrzebować (na przykład <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> uprawnień).  
  
 Aby przetestować kod, który można będzie wydawać uruchamianego tylko w środowiskach częściowo zaufanym umożliwia także tryb piaskownicy.  
  
 <xref:System.AppDomain> Jest skutecznym sposobem zapewnienia piaskownicy dla zarządzanych aplikacji. Domeny aplikacji, które są używane do uruchamiania częściowo zaufanego kodu mają uprawnienia, które definiują chronionych zasobów, które są dostępne podczas uruchamiania w ramach którego <xref:System.AppDomain>. Kod, który działa wewnątrz <xref:System.AppDomain> jest ograniczone przez uprawnienia związane z <xref:System.AppDomain> i będzie mógł uzyskać dostęp tylko określonych zasobów. <xref:System.AppDomain> Obejmuje również <xref:System.Security.Policy.StrongName> tablica, która służy do identyfikowania zestawów, które mają być załadowany jako w pełni zaufany. Dzięki temu twórca <xref:System.AppDomain> można uruchomić nowej domeny piaskownicy, umożliwiająca pomocnika określonych zestawów jako w pełni zaufane. Innym rozwiązaniem do ładowania zestawów jako w pełni zaufane jest umieszczenie ich w globalnej pamięci podręcznej; Jednakże, zostaną załadowane zestawy jako w pełni zaufany we wszystkich domenach aplikacji, utworzony na tym komputerze. Lista silnej nazwy obsługuje na-<xref:System.AppDomain> decyzji, który zapewnia bardziej restrykcyjne określenie.  
  
 Możesz użyć <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> przeciążenia metody, aby określić uprawnienia ustawione dla aplikacji działających w piaskownicy. Tego przeciążenia można określić dokładny poziom zabezpieczeń dostępu kodu, który ma. Zestawy, które są ładowane do <xref:System.AppDomain> przy użyciu tego przeciążenia można albo mieć określony tylko zestaw uprawnień lub może być w pełni zaufany. Zestaw jest udzielone pełne zaufanie, jeśli znajduje się w globalnej pamięci podręcznej lub na liście `fullTrustAssemblies` ( <xref:System.Security.Policy.StrongName>) parametr tablicy. Tylko zestawy znane jako w pełni zaufany, powinny zostać dodane do `fullTrustAssemblies` listy.  
  
 Przeciążenie ma następujący podpis:  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 Parametry <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> przeciążenia metody umożliwia określenie nazwy <xref:System.AppDomain>, dowód <xref:System.AppDomain>, <xref:System.AppDomainSetup> obiektu, który identyfikuje podstawa aplikacji piaskownicy, zestaw uprawnień, aby użyć i silne nazwy dla całkowicie zaufanych zestawów.  
  
 Ze względów bezpieczeństwa podstawy aplikacji określony w `info` parametrów nie powinny być podstawowy dla aplikacji macierzystej aplikacji.  
  
 Dla `grantSet` parametru, można określić zestaw uprawnień, utworzono jawnie lub standardowe uprawnienie zestaw utworzony przez <xref:System.Security.SecurityManager.GetStandardSandbox%2A> metody.  
  
 W przeciwieństwie do większości <xref:System.AppDomain> ładuje dowodów dla <xref:System.AppDomain> (inaczej niż w `securityInfo` parametr) nie jest używana do określenia przyznanego zestawu dla częściowo zaufanych zestawów. Zamiast tego niezależnie jest określona przez `grantSet` parametru. Jednak dowód może służyć do innych celów, takich jak określanie zakresu wydzielonej pamięci masowej.  
  
### <a name="to-run-an-application-in-a-sandbox"></a>Aby uruchomić aplikację w bibliotece  
  
1.  Utwórz zestaw uprawnień, aby można mu było przydzielić niezaufanych aplikacji. Jest co najmniej uprawnienie można przyznać <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> uprawnień. Możesz też przyznawać dodatkowe uprawnienia, które Twoim zdaniem mogą być bezpieczne dla niezaufanego kodu; na przykład <xref:System.Security.Permissions.IsolatedStorageFilePermission>. Poniższy kod tworzy nowy zestaw uprawnień o tylko <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> uprawnienia.  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     Alternatywnie można użyć istniejącego nazwany zestaw uprawnień, takich jak Internet.  
  
    ```  
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <xref:System.Security.SecurityManager.GetStandardSandbox%2A> Metoda zwraca albo `Internet` zestaw uprawnień lub `LocalIntranet` uprawnienia w zależności od strefy w dowodów. <xref:System.Security.SecurityManager.GetStandardSandbox%2A> tworzy również uprawnienia tożsamości dla niektórych obiektów dowód przekazywane jako odwołania.  
  
2.  Podpisz zestaw, który zawiera klasę hostingu (o nazwie `Sandboxer` w tym przykładzie), wywołuje niezaufanego kodu. Dodaj <xref:System.Security.Policy.StrongName> używany do podpisywania zestawu do <xref:System.Security.Policy.StrongName> tablicę `fullTrustAssemblies` parametru <xref:System.AppDomain.CreateDomain%2A> wywołania. Klasa hostingu musi działać jako w pełni zaufany, aby włączyć wykonywanie częściowo zaufanemu kodowi lub oferty usług do aplikacji częściowego zaufania. Jest to, jak odczytać <xref:System.Security.Policy.StrongName> zestawu:  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     Nie masz zestawów .NET framework, takich jak mscorlib i System.dll ma zostać dodany do listy pełnego zaufania, ponieważ są one załadowane jako w pełni zaufany z globalnej pamięci podręcznej.  
  
3.  Inicjowanie <xref:System.AppDomainSetup> parametru <xref:System.AppDomain.CreateDomain%2A> metody. Z tego parametru można kontrolować wiele ustawień nowej <xref:System.AppDomain>. <xref:System.AppDomainSetup.ApplicationBase%2A> Właściwość jest ważne ustawienia i powinna być inna niż <xref:System.AppDomainSetup.ApplicationBase%2A> właściwość <xref:System.AppDomain> hostingu aplikacji. Jeśli <xref:System.AppDomainSetup.ApplicationBase%2A> ustawień są takie same, aplikacja częściowego zaufania może uzyskać ładowanie (jako w pełni zaufany) wyjątek, który definiuje, w związku z tym pełniejsze wykorzystanie hostingu aplikacji. Jest to kolejny powód, dlaczego catch (exception) nie jest zalecane. Ustawienie aplikacji base hosta różni się od podstawy aplikacji dla aplikacji w trybie piaskownicy zmniejsza ryzyko luki w zabezpieczeniach.  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4.  Wywołaj <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> przeciążenia metody tworzenia domeny aplikacji przy użyciu parametrów została określona.  
  
     Podpis dla tej metody jest:  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,   
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,   
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     Informacje dodatkowe:  
  
    -   Jest to jedyna przeciążenia <xref:System.AppDomain.CreateDomain%2A> metody, która przyjmuje <xref:System.Security.PermissionSet> jako parametr, a zatem jedynym przeciążenia, które umożliwia ładowanie aplikacji w środowisku częściowego zaufania.  
  
    -   `evidence` Parametr nie jest używany do obliczania zestawu uprawnień; jest używany do identyfikacji przez inne funkcje programu .NET Framework.  
  
    -   Ustawienie <xref:System.AppDomainSetup.ApplicationBase%2A> właściwość `info` parametr jest obowiązkowy w przypadku tego przeciążenia.  
  
    -   `fullTrustAssemblies` Parametr ma `params` — słowo kluczowe, co oznacza, że nie jest niezbędne do utworzenia <xref:System.Security.Policy.StrongName> tablicy. Przekazywanie jako parametrów 0, 1 lub więcej silnych nazw jest dozwolona.  
  
    -   Kod, aby utworzyć domenę aplikacji to:  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5.  Ładowanie kodu do piaskownicy <xref:System.AppDomain> utworzony. Można to zrobić na dwa sposoby:  
  
    -   Wywołaj <xref:System.AppDomain.ExecuteAssembly%2A> metody dla zestawu.  
  
    -   Użyj <xref:System.Activator.CreateInstanceFrom%2A> metodę, aby utworzyć wystąpienie klasy pochodne <xref:System.MarshalByRefObject> w nowym <xref:System.AppDomain>.  
  
     Druga metoda jest preferowana, ponieważ ułatwia do przekazania parametrów do nowego <xref:System.AppDomain> wystąpienia. <xref:System.Activator.CreateInstanceFrom%2A> Metoda zapewnia dwie ważne funkcje:  
  
    -   Możesz użyć bazy kodu, który wskazuje na lokalizację, która nie zawiera zestawu.  
  
    -   Masz możliwości tworzenia w obszarze <xref:System.Security.CodeAccessPermission.Assert%2A> dla pełnego zaufania (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), która pozwala na tworzenie wystąpienia klasy krytycznych. (Jest to wykonywane zawsze, gdy zestaw ma oznaczenia nie przezroczystości, a także jest ładowany jako w pełni zaufany.) W związku z tym musisz być ostrożnym, aby utworzyć kod, którym ufasz, że za pomocą tej funkcji i zaleca się utworzenie tylko wystąpienia klasy w pełni zaufany w nowej domenie aplikacji.  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     Należy pamiętać, aby można było utworzyć wystąpienia klasy w nowej domenie, klasa ma rozszerzenie <xref:System.MarshalByRefObject> klasy  
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6.  Dekodowanie nowe wystąpienie domeny do odwołania w tej domenie. Ta dokumentacja jest używany do wykonania niezaufanego kodu.  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7.  Wywołaj `ExecuteUntrustedCode` metody w wystąpieniu `Sandboxer` klasy właśnie utworzony.  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     To wywołanie jest wykonywane w domenie aplikacji w trybie piaskownicy ma ograniczone uprawnienia.  
  
    ```csharp
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
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
    ```  
  
     <xref:System.Reflection> Służy do uzyskać dojścia do metody w częściowo zaufanym zestawem. Uchwyt może służyć do wykonywania kodu w bezpieczny sposób za pomocą minimalny poziom uprawnień.  
  
     W poprzednim kodzie, należy pamiętać, <xref:System.Security.PermissionSet.Assert%2A> uprawnienia pełnego zaufania, przed rozpoczęciem drukowania <xref:System.Security.SecurityException>.  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     Asercja pełnego zaufania jest używany do uzyskiwania rozszerzonych informacji z <xref:System.Security.SecurityException>. Bez <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.SecurityException.ToString%2A> metody <xref:System.Security.SecurityException> wykryje, że jest częściowo zaufany kod w stosie i ograniczyć zwracane informacje dotyczą. Może to spowodować problemy z zabezpieczeniami, jeśli częściowo zaufanemu kodowi można odczytać te informacje, ale ryzyko skuteczność została osłabiona przez nieprzyznanie <xref:System.Security.Permissions.UIPermission>. Asercja pełnego zaufania należy używać oszczędnie i tylko wtedy, gdy masz pewność, że nie umożliwi częściowo zaufanemu kodowi do podniesienia uprawnień na w pełni zaufany. Zgodnie z zasadą nie wymagają kodu, której nie ufasz w tej samej funkcji i asercja wywołuje się, aby uzyskać pełne zaufanie. Jest dobrą praktyką, aby zawsze wracają assert, po zakończeniu korzystania z niego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wykonuje procedurę w poprzedniej sekcji. W tym przykładzie projekt o nazwie `Sandboxer` w programie Visual Studio rozwiązanie zawiera także projekt o nazwie `UntrustedCode`, który implementuje klasa `UntrustedClass`. W tym scenariuszu przyjmuje się, czy zostały pobrane zestawu biblioteki, zawierający metodę, która powinna zwrócić `true` lub `false` do wskazania, czy liczba podane jest liczbą Fibonacci. Zamiast tego metoda próbuje odczytać plik z komputera. Poniższy przykład pokazuje niezaufanego kodu.  
  
```csharp
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
  
 W poniższym przykładzie przedstawiono `Sandboxer` kod aplikacji, która wykonuje niezaufanego kodu.  
  
```csharp
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
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz także
- [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
