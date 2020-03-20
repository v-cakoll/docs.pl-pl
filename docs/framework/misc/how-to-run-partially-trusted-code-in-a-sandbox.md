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
ms.openlocfilehash: b2f5a72e747f6c71743a7b22fe9f1962ac2f6b53
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181178"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a>Porady: uruchamianie częściowo zaufanego kodu w bibliotece
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Piaskownica jest praktyką uruchamiania kodu w ograniczonym środowisku zabezpieczeń, co ogranicza uprawnienia dostępu przyznane do kodu. Na przykład jeśli masz bibliotekę zarządzaną ze źródła, któremu nie ufasz całkowicie, nie należy jej uruchamiać jako w pełni zaufanej. Zamiast tego należy umieścić kod w obszarze izolowanym, który ogranicza jego uprawnienia do <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> tych, które oczekują, że będzie potrzebne (na przykład uprawnienia).  
  
 Można również użyć piaskownicy do testowania kodu, który będzie dystrybuowany, który będzie uruchamiany w częściowo zaufanych środowiskach.  
  
 An <xref:System.AppDomain> jest skutecznym sposobem zapewnienia piaskownicy dla aplikacji zarządzanych. Domeny aplikacji, które są używane do uruchamiania częściowo zaufanego kodu mają uprawnienia, <xref:System.AppDomain>które definiują chronione zasoby, które są dostępne podczas uruchamiania w tym . Kod, który <xref:System.AppDomain> działa wewnątrz jest związany uprawnieniami <xref:System.AppDomain> skojarzonymi z i może uzyskać dostęp tylko do określonych zasobów. Zawiera <xref:System.AppDomain> również <xref:System.Security.Policy.StrongName> tablicę, która jest używana do identyfikowania zestawów, które mają być ładowane jako w pełni zaufane. Dzięki temu twórca, <xref:System.AppDomain> aby rozpocząć nową domenę w trybie piaskownicy, która umożliwia określone zestawy pomocnika być w pełni zaufany. Inną opcją ładowania zestawów jako w pełni zaufanych jest umieszczenie ich w globalnej pamięci podręcznej zestawów; jednak, że będzie załadować zestawy jako w pełni zaufane we wszystkich domenach aplikacji utworzonych na tym komputerze. Lista silnych nazwisk popiera<xref:System.AppDomain> decyzję per- która zapewnia bardziej restrykcyjną determinację.  
  
 Przeciążenie <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> metody służy do określenia zestawu uprawnień dla aplikacji, które są uruchamiane w obszarze izolowanym. To przeciążenie umożliwia określenie dokładnego poziomu zabezpieczeń dostępu do kodu, które chcesz. Zestawy, które są <xref:System.AppDomain> ładowane do za pomocą tego przeciążenia może mieć tylko określony zestaw dotacji lub mogą być w pełni zaufane. Zestaw otrzymuje pełne zaufanie, jeśli znajduje się w globalnej `fullTrustAssemblies` pamięci <xref:System.Security.Policy.StrongName>podręcznej zestawów lub jest wymieniony w () parametr tablicy. Do listy należy dodać tylko zestawy, `fullTrustAssemblies` o których wiadomo, że są w pełni zaufane.  
  
 Przeciążenie ma następujący podpis:  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> Parametry przeciążenia metody określają nazwę <xref:System.AppDomain>, dowód dla <xref:System.AppDomain>obiektu, który identyfikuje bazę <xref:System.AppDomainSetup> aplikacji dla piaskownicy, ustawione uprawnienia do użycia i silne nazwy w pełni zaufanych zestawów.  
  
 Ze względów bezpieczeństwa baza `info` aplikacji określona w parametrze nie powinna być podstawą aplikacji hostingowej.  
  
 Dla `grantSet` parametru można określić zestaw uprawnień, który został jawnie utworzony, <xref:System.Security.SecurityManager.GetStandardSandbox%2A> lub standardowy zestaw uprawnień utworzony przez metodę.  
  
 W <xref:System.AppDomain> przeciwieństwie do większości obciążeń <xref:System.AppDomain> dowody dla (który jest dostarczany przez `securityInfo` parametr) nie jest używany do określenia zestawu dotacji dla częściowo zaufanych zestawów. Zamiast tego jest niezależnie określony `grantSet` przez parametr. Jednak dowody mogą być używane do innych celów, takich jak określenie zakresu izolowanego magazynu.  
  
### <a name="to-run-an-application-in-a-sandbox"></a>Aby uruchomić aplikację w piaskownicy  
  
1. Utwórz zestaw uprawnień, które mają zostać przyznane niezaufanej aplikacji. Minimalne uprawnienie, które <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> można udzielić, to uprawnienie. Można również udzielić dodatkowych uprawnień, które uważasz za bezpieczne dla niezaufanego kodu; na przykład <xref:System.Security.Permissions.IsolatedStorageFilePermission>. Poniższy kod tworzy nowy zestaw <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> uprawnień tylko z uprawnieniami.  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     Alternatywnie można użyć istniejącego nazwanego zestawu uprawnień, takiego jak Internet.  
  
    ```csharp
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     Metoda <xref:System.Security.SecurityManager.GetStandardSandbox%2A> zwraca zestaw `Internet` uprawnień lub `LocalIntranet` zestaw uprawnień w zależności od strefy w dowodach. <xref:System.Security.SecurityManager.GetStandardSandbox%2A>również konstruuje uprawnienia tożsamości dla niektórych obiektów dowodów przekazanych jako odwołania.  
  
2. Podpisz zestaw, który zawiera `Sandboxer` klasę hostingu (o nazwie w tym przykładzie), która wywołuje niezaufany kod. Dodaj <xref:System.Security.Policy.StrongName> używane do podpisania zestawu <xref:System.Security.Policy.StrongName> do `fullTrustAssemblies` tablicy <xref:System.AppDomain.CreateDomain%2A> parametru wywołania. Klasa hostingu musi działać jako w pełni zaufany, aby umożliwić wykonanie kodu częściowego zaufania lub oferować usługi aplikacji częściowego zaufania. W ten sposób <xref:System.Security.Policy.StrongName> można odczytać zestawu:  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     Zestawy .NET Framework, takie jak mscorlib i System.dll, nie muszą być dodawane do listy pełnego zaufania, ponieważ są ładowane jako w pełni zaufane z globalnej pamięci podręcznej zestawów.  
  
3. Zainicjować <xref:System.AppDomainSetup> parametr <xref:System.AppDomain.CreateDomain%2A> metody. Za pomocą tego parametru można kontrolować wiele <xref:System.AppDomain>ustawień nowego . Właściwość <xref:System.AppDomainSetup.ApplicationBase%2A> jest ważnym ustawieniem i powinna <xref:System.AppDomainSetup.ApplicationBase%2A> się <xref:System.AppDomain> różnić od właściwości aplikacji hostingowej. Jeśli <xref:System.AppDomainSetup.ApplicationBase%2A> ustawienia są takie same, aplikacja częściowego zaufania można uzyskać aplikacji hostingu, aby załadować (jako w pełni zaufany) wyjątek, który definiuje, wykorzystując go. Jest to kolejny powód, dla którego catch (wyjątek) nie jest zalecane. Ustawienie bazy aplikacji hosta inaczej niż baza aplikacji w trybie piaskownicy zmniejsza ryzyko exploitów.  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. Wywołanie <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> przeciążenia metody, aby utworzyć domenę aplikacji przy użyciu parametrów, które określiliśmy.  
  
     Podpis dla tej metody jest:  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     Informacje dodatkowe:  
  
    - Jest to tylko przeciążenie <xref:System.AppDomain.CreateDomain%2A> metody, <xref:System.Security.PermissionSet> która przyjmuje jako parametr, a tym samym tylko przeciążenie, które pozwala załadować aplikację w ustawieniach częściowego zaufania.  
  
    - Parametr `evidence` nie jest używany do obliczania zestawu uprawnień; służy do identyfikacji przez inne funkcje programu .NET Framework.  
  
    - Ustawienie <xref:System.AppDomainSetup.ApplicationBase%2A> właściwości parametru `info` jest obowiązkowe dla tego przeciążenia.  
  
    - Parametr `fullTrustAssemblies` zawiera `params` słowo kluczowe, co oznacza, że <xref:System.Security.Policy.StrongName> nie jest konieczne tworzenie tablicy. Przekazywanie 0, 1 lub więcej silnych nazw jako parametry jest dozwolone.  
  
    - Kod do utworzenia domeny aplikacji jest:  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. Załaduj kod <xref:System.AppDomain> do utworzonego piaskownicy. Można to zrobić na dwa sposoby:  
  
    - Wywołanie <xref:System.AppDomain.ExecuteAssembly%2A> metody dla zestawu.  
  
    - Użyj <xref:System.Activator.CreateInstanceFrom%2A> metody, aby utworzyć wystąpienie klasy <xref:System.MarshalByRefObject> pochodnej <xref:System.AppDomain>w nowym .  
  
     Druga metoda jest preferowana, ponieważ ułatwia przekazywanie parametrów <xref:System.AppDomain> do nowego wystąpienia. Metoda <xref:System.Activator.CreateInstanceFrom%2A> ta zapewnia dwie ważne cechy:  
  
    - Można użyć bazy kodu, który wskazuje lokalizację, która nie zawiera zestawu.  
  
    - Tworzenie można wykonać w <xref:System.Security.CodeAccessPermission.Assert%2A> ramach for<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>full-trust ( ), który umożliwia utworzenie wystąpienia klasy krytycznej. (Dzieje się tak, gdy zespół nie ma oznaczeń przezroczystości i jest ładowany jako w pełni zaufany). W związku z tym należy uważać, aby utworzyć tylko kod, który można ufać z tej funkcji i zaleca się tworzenie tylko wystąpienia w pełni zaufanych klas w nowej domenie aplikacji.  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     Należy zauważyć, że aby utworzyć wystąpienie klasy w nowej domenie, klasa musi rozszerzyć <xref:System.MarshalByRefObject> klasę  
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. Odrapuj nowe wystąpienie domeny na odwołanie w tej domenie. To odwołanie jest używane do wykonywania niezaufanego kodu.  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. Wywołanie `ExecuteUntrustedCode` metody w wystąpieniu klasy, `Sandboxer` która właśnie została utworzona.  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     To wywołanie jest wykonywane w domenie aplikacji w trybie piaskownicy, która ma ograniczone uprawnienia.  
  
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
  
     <xref:System.Reflection>służy do uzyskania dojścia metody w zestawie częściowo zaufanych. Dojście może służyć do wykonywania kodu w bezpieczny sposób z minimalnymi uprawnieniami.  
  
     W poprzednim kodzie <xref:System.Security.PermissionSet.Assert%2A> zanotuj uprawnienie pełnego <xref:System.Security.SecurityException>zaufania przed wydrukowaniem pliku .  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     Potwierdzenie pełnego zaufania służy do uzyskiwania rozszerzonych informacji z pliku <xref:System.Security.SecurityException>. Bez <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.SecurityException.ToString%2A> metoda <xref:System.Security.SecurityException> odkryje, że istnieje częściowo zaufany kod na stosie i ograniczy zwracane informacje. Może to spowodować problemy z zabezpieczeniami, jeśli kod częściowego zaufania może odczytać <xref:System.Security.Permissions.UIPermission>te informacje, ale ryzyko jest ograniczone przez nieudzielenie . Potwierdzenie pełnego zaufania powinny być używane oszczędnie i tylko wtedy, gdy masz pewność, że nie zezwalasz na częściowe zaufanie kodu podnieść do pełnego zaufania. Z reguły nie należy wywoływać kodu, którego nie ufasz w tej samej funkcji i po wywołaniu potwierdzenia dla pełnego zaufania. Jest dobrą praktyką, aby zawsze przywrócić potwierdzenia po zakończeniu korzystania z niego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład implementuje procedurę w poprzedniej sekcji. W przykładzie projekt `Sandboxer` o nazwie w rozwiązaniu programu `UntrustedCode`Visual Studio zawiera `UntrustedClass`również projekt o nazwie , który implementuje klasę . W tym scenariuszu założono, że pobrano zestaw biblioteki `true` zawierający metodę, która ma zwrócić lub `false` wskazać, czy podana liczba jest numerem Fibonacciego. Zamiast tego metoda próbuje odczytać plik z komputera. W poniższym przykładzie pokazano niezaufany kod.  
  
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
  
 W poniższym `Sandboxer` przykładzie pokazano kod aplikacji, który wykonuje niezaufany kod.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Wytyczne dotyczące bezpiecznego programowania](../../standard/security/secure-coding-guidelines.md)
