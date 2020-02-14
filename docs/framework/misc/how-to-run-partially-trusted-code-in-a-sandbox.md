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
ms.openlocfilehash: 0191846f5589b0162ba342161fb5919ff20099d4
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215862"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a>Porady: uruchamianie częściowo zaufanego kodu w bibliotece
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Tryb piaskownicy jest praktycznym sposobem uruchamiania kodu w ograniczonym środowisku zabezpieczeń, który ogranicza uprawnienia dostępu przyznane do kodu. Na przykład, jeśli masz bibliotekę zarządzaną z źródła, które nie jest całkowicie zaufane, nie należy uruchamiać go jako w pełni zaufany. Zamiast tego należy umieścić kod w piaskownicy, który ogranicza jego uprawnienia do tych, których oczekuje potrzeba (na przykład <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> uprawnienia).  
  
 Możesz również użyć piaskownicy do testowania kodu, który będzie wykonywany w środowiskach częściowo zaufanych.  
  
 <xref:System.AppDomain> jest skutecznym sposobem udostępniania piaskownicy dla aplikacji zarządzanych. Domeny aplikacji używane do uruchamiania częściowo zaufanego kodu mają uprawnienia definiujące chronione zasoby, które są dostępne podczas uruchamiania w ramach tego <xref:System.AppDomain>. Kod, który jest uruchamiany w <xref:System.AppDomain> jest powiązany z uprawnieniami skojarzonymi z <xref:System.AppDomain> i może uzyskiwać dostęp tylko do określonych zasobów. <xref:System.AppDomain> zawiera również tablicę <xref:System.Security.Policy.StrongName>, która jest używana do identyfikowania zestawów, które mają zostać załadowane jako w pełni zaufane. Umożliwia to twórcy <xref:System.AppDomain> uruchamiania nowej domeny w trybie piaskownicy, która umożliwia pełne zaufane zestawy pomocnika. Kolejną opcją ładowania zestawów jako w pełni zaufanej jest umieszczenie ich w globalnej pamięci podręcznej zestawów; Jednak program będzie ładować zestawy jako w pełni zaufane we wszystkich domenach aplikacji utworzonych na tym komputerze. Lista silnych nazw obsługuje decyzję dla<xref:System.AppDomain>, która zapewnia bardziej restrykcyjne Określanie.  
  
 Można użyć przeciążenia metody <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType>, aby określić zestaw uprawnień dla aplikacji, które działają w piaskownicy. To przeciążenie umożliwia określenie dokładnego poziomu zabezpieczeń dostępu kodu. Zestawy, które są ładowane do <xref:System.AppDomain> przy użyciu tego przeciążenia, mogą mieć określony zestaw dotacji lub mogą być w pełni zaufane. Zestaw uzyskuje pełne zaufanie, jeśli znajduje się w globalnej pamięci podręcznej zestawów lub znajduje się w `fullTrustAssemblies` (<xref:System.Security.Policy.StrongName>) parametr tablicy. Do listy `fullTrustAssemblies` należy dodać tylko zestawy znane jako w pełni zaufane.  
  
 Przeciążenie ma następujący podpis:  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 Parametry przeciążenia metody <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> określają nazwę <xref:System.AppDomain>, dowody dla <xref:System.AppDomain>, obiekt <xref:System.AppDomainSetup>, który identyfikuje bazę aplikacji dla piaskownicy, zestaw uprawnień, który ma być używany, oraz silne nazwy dla w pełni zaufanych zestawów.  
  
 Ze względów bezpieczeństwa baza aplikacji określona w parametrze `info` nie powinna być bazą aplikacji dla aplikacji hostingowej.  
  
 Dla parametru `grantSet` można określić zestaw uprawnień, który został utworzony jawnie, lub standardowy zestaw uprawnień utworzony przez metodę <xref:System.Security.SecurityManager.GetStandardSandbox%2A>.  
  
 W przeciwieństwie do większości obciążeń <xref:System.AppDomain>, dowody dla <xref:System.AppDomain> (które są dostarczane przez parametr `securityInfo`) nie są używane do określenia zestawu dotacji dla częściowo zaufanych zestawów. Zamiast tego jest on niezależnie określony przez parametr `grantSet`. Jednakże dowody mogą być używane do innych celów, takich jak określenie zakresu izolowanego magazynu.  
  
### <a name="to-run-an-application-in-a-sandbox"></a>Aby uruchomić aplikację w piaskownicy  
  
1. Utwórz zestaw uprawnień, który ma zostać udzielony dla niezaufanej aplikacji. Minimalnym uprawnieniem, które można udzielić, jest uprawnienie <xref:System.Security.Permissions.SecurityPermissionFlag.Execution>. Możesz również udzielić dodatkowych uprawnień, które mogą być bezpieczne dla niezaufanego kodu; na przykład <xref:System.Security.Permissions.IsolatedStorageFilePermission>. Poniższy kod tworzy nowy zestaw uprawnień z uprawnieniami tylko <xref:System.Security.Permissions.SecurityPermissionFlag.Execution>.  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     Alternatywnie możesz użyć istniejącego zestawu uprawnień o nazwie, takiego jak Internet.  
  
    ```csharp
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     Metoda <xref:System.Security.SecurityManager.GetStandardSandbox%2A> zwraca zestaw uprawnień `Internet` lub zestaw uprawnień `LocalIntranet` w zależności od strefy w zeznaniach. <xref:System.Security.SecurityManager.GetStandardSandbox%2A> również konstruuje uprawnienia tożsamości dla niektórych obiektów dowodu przesłanych jako odwołania.  
  
2. Podpisz zestaw zawierający klasę hostingu (o nazwie `Sandboxer` w tym przykładzie), która wywołuje niezaufany kod. Dodaj <xref:System.Security.Policy.StrongName> używany do podpisywania zestawu do tablicy <xref:System.Security.Policy.StrongName> `fullTrustAssemblies` parametru wywołania <xref:System.AppDomain.CreateDomain%2A>. Klasa hostingu musi działać jako w pełni zaufana, aby umożliwić wykonywanie kodu częściowego zaufania lub oferowanie usług dla aplikacji częściowo zaufanej. Jest to sposób odczytywania <xref:System.Security.Policy.StrongName> zestawu:  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     Zestawy .NET Framework, takie jak mscorlib i system. dll, nie muszą być dodawane do listy całkowicie zaufanych, ponieważ są załadowane jako w pełni zaufane z globalnej pamięci podręcznej zestawów.  
  
3. Zainicjuj <xref:System.AppDomainSetup> parametr metody <xref:System.AppDomain.CreateDomain%2A>. Za pomocą tego parametru można kontrolować wiele ustawień nowego <xref:System.AppDomain>. Właściwość <xref:System.AppDomainSetup.ApplicationBase%2A> jest ważnym ustawieniem i powinna być inna niż Właściwość <xref:System.AppDomainSetup.ApplicationBase%2A> dla <xref:System.AppDomain> aplikacji hostingowej. Jeśli ustawienia <xref:System.AppDomainSetup.ApplicationBase%2A> są takie same, aplikacja częściowej relacji zaufania może pobrać aplikację hostingu (jako w pełni zaufana), którą definiuje wyjątek, a tym samym ją wykorzystać. Jest to kolejny powód, dla którego nie zaleca się przechwytywania (wyjątek). Ustawienie bazy aplikacji hosta różni się od bazy aplikacji w aplikacji w trybie piaskownicy, co zmniejsza ryzyko ataków wykorzystujących luki w zabezpieczeniach.  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. Wywołaj Przeciążenie metody <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29>, aby utworzyć domenę aplikacji przy użyciu określonych parametrów.  
  
     Sygnaturą tej metody jest:  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,   
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,   
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     Informacje dodatkowe:  
  
    - Jest to jedyne Przeciążenie metody <xref:System.AppDomain.CreateDomain%2A>, która przyjmuje <xref:System.Security.PermissionSet> jako parametr, i w ten sposób jedynym przeciążeniem umożliwiającym załadowanie aplikacji w ustawieniu częściowej relacji zaufania.  
  
    - Parametr `evidence` nie jest używany do obliczania zestawu uprawnień; służy do identyfikacji przez inne funkcje .NET Framework.  
  
    - Ustawienie właściwości <xref:System.AppDomainSetup.ApplicationBase%2A> parametru `info` jest obowiązkowe dla tego przeciążenia.  
  
    - `fullTrustAssemblies` parametr zawiera słowo kluczowe `params`, co oznacza, że nie jest konieczne tworzenie tablicy <xref:System.Security.Policy.StrongName>. Przekazanie wartości 0, 1 lub większej liczby silnych nazw jako parametrów jest dozwolone.  
  
    - Kod do utworzenia domeny aplikacji:  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. Załaduj kod do utworzonego <xref:System.AppDomain> piaskownicy. Można to zrobić na dwa sposoby:  
  
    - Wywołaj metodę <xref:System.AppDomain.ExecuteAssembly%2A> zestawu.  
  
    - Użyj metody <xref:System.Activator.CreateInstanceFrom%2A>, aby utworzyć wystąpienie klasy pochodzącej od <xref:System.MarshalByRefObject> w nowym <xref:System.AppDomain>.  
  
     Druga metoda jest preferowana, ponieważ ułatwia przekazywanie parametrów do nowego wystąpienia <xref:System.AppDomain>. Metoda <xref:System.Activator.CreateInstanceFrom%2A> zapewnia dwie ważne funkcje:  
  
    - Możesz użyć bazy kodu, która wskazuje lokalizację, która nie zawiera Twojego zestawu.  
  
    - Tworzenie można wykonać w ramach <xref:System.Security.CodeAccessPermission.Assert%2A> dla pełnego zaufania (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), co umożliwia utworzenie wystąpienia klasy krytycznej. (Dzieje się tak, gdy zestaw nie ma znaczników przezroczystości i jest ładowany jako w pełni zaufany). W związku z tym należy zachować ostrożność, aby utworzyć tylko kod, który ufasz tej funkcji, i zalecamy utworzenie tylko wystąpień w pełni zaufanych klas w nowej domenie aplikacji.  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     Należy pamiętać, że w celu utworzenia wystąpienia klasy w nowej domenie Klasa musi zwiększyć klasę <xref:System.MarshalByRefObject>  
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. Odpakuj nowe wystąpienie domeny do odwołania w tej domenie. To odwołanie służy do wykonywania niezaufanego kodu.  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. Wywołaj metodę `ExecuteUntrustedCode` w wystąpieniu klasy `Sandboxer`, która została właśnie utworzona.  
  
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
  
     <xref:System.Reflection> służy do uzyskania dojścia metody w częściowo zaufanym zestawie. Uchwyt może służyć do wykonywania kodu w bezpieczny sposób z minimalnymi uprawnieniami.  
  
     Przed przystąpieniem do drukowania <xref:System.Security.SecurityException>w poprzednim kodzie Zwróć uwagę na <xref:System.Security.PermissionSet.Assert%2A> uprawnienia pełnego zaufania.  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     Potwierdzenie pełnego zaufania służy do uzyskiwania rozszerzonych informacji z <xref:System.Security.SecurityException>. Bez <xref:System.Security.PermissionSet.Assert%2A>Metoda <xref:System.Security.SecurityException.ToString%2A> <xref:System.Security.SecurityException> wykrywa, że na stosie znajduje się częściowo zaufany kod i ograniczy zwrócone informacje. Może to spowodować problemy z bezpieczeństwem, jeśli kod częściowego zaufania może odczytać te informacje, ale ryzyko to nie jest przyznawane <xref:System.Security.Permissions.UIPermission>. Potwierdzenie pełnego zaufania powinno być używane oszczędnie i tylko wtedy, gdy masz pewność, że nie zezwolisz na podniesienie poziomu kodu zaufania do pełnego zaufania. Zgodnie z regułą nie należy wywoływać kodu, który nie jest zaufany w tej samej funkcji, i po wywołaniu potwierdzenia pełnego zaufania. Dobrym sposobem jest zawsze przywrócenie potwierdzenia po zakończeniu korzystania z niego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład implementuje procedurę opisaną w poprzedniej sekcji. W przykładzie projekt o nazwie `Sandboxer` w rozwiązaniu programu Visual Studio zawiera również projekt o nazwie `UntrustedCode`, który implementuje klasę `UntrustedClass`. W tym scenariuszu przyjęto założenie, że pobrano zestaw biblioteczny zawierający metodę, która powinna zwracać `true` lub `false`, aby wskazać, czy podany numer jest numerem Fibonacci. Zamiast tego Metoda próbuje odczytać plik z komputera. Poniższy przykład pokazuje kod niezaufany.  
  
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
  
 W poniższym przykładzie pokazano kod aplikacji `Sandboxer`, który wykonuje kod niezaufany.  
  
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
