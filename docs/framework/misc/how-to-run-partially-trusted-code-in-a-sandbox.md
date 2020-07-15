---
title: 'Porady: uruchamianie częściowo zaufanego kodu w bibliotece'
description: Odkryj, jak uruchomić częściowo zaufany kod w piaskownicy w programie .NET. Klasa AppDomain jest efektywnym sposobem aplikacji zarządzanych w trybie piaskownicy.
ms.date: 03/30/2017
helpviewer_keywords:
- partially trusted code
- sandboxing
- partial trust
- restricted security environment
- code security, sandboxing
ms.assetid: d1ad722b-5b49-4040-bff3-431b94bb8095
ms.openlocfilehash: e02b5d679fb1f5947373399ac1226732623ef96d
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309238"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a>Porady: uruchamianie częściowo zaufanego kodu w bibliotece
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Tryb piaskownicy jest praktycznym sposobem uruchamiania kodu w ograniczonym środowisku zabezpieczeń, który ogranicza uprawnienia dostępu przyznane do kodu. Na przykład, jeśli masz bibliotekę zarządzaną z źródła, które nie jest całkowicie zaufane, nie należy uruchamiać go jako w pełni zaufany. Zamiast tego należy umieścić kod w piaskownicy, który ogranicza jego uprawnienia do tych, których oczekujesz (na przykład <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> uprawnienia).  
  
 Możesz również użyć piaskownicy do testowania kodu, który będzie wykonywany w środowiskach częściowo zaufanych.  
  
 <xref:System.AppDomain>Jest skutecznym sposobem zapewnienia piaskownicy dla aplikacji zarządzanych. Domeny aplikacji używane do uruchamiania częściowo zaufanego kodu mają uprawnienia, które definiują chronione zasoby, które są dostępne podczas działania w ramach tego programu <xref:System.AppDomain> . Kod, który jest uruchamiany w ramach programu, <xref:System.AppDomain> jest powiązany z uprawnieniami skojarzonymi z <xref:System.AppDomain> i ma zezwolenie na dostęp tylko do określonych zasobów. <xref:System.AppDomain>Zawiera również <xref:System.Security.Policy.StrongName> tablicę, która jest używana do identyfikowania zestawów, które mają zostać załadowane jako w pełni zaufane. Dzięki temu Twórca programu <xref:System.AppDomain> może rozpocząć nową domenę w trybie piaskownicy, która pozwala na pełne ufanie określonym zestawom pomocnika. Kolejną opcją ładowania zestawów jako w pełni zaufanej jest umieszczenie ich w globalnej pamięci podręcznej zestawów; Jednak program będzie ładować zestawy jako w pełni zaufane we wszystkich domenach aplikacji utworzonych na tym komputerze. Lista silnych nazw obsługuje <xref:System.AppDomain> podjęcie decyzji, która zapewnia bardziej restrykcyjne Określanie.  
  
 Można użyć <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> przeciążenia metody, aby określić zestaw uprawnień dla aplikacji, które działają w piaskownicy. To przeciążenie umożliwia określenie dokładnego poziomu zabezpieczeń dostępu kodu. Zestawy, które są ładowane do programu <xref:System.AppDomain> przy użyciu tego przeciążenia, mogą mieć określony zestaw dotacji lub mogą być w pełni zaufane. Zestaw uzyskuje pełne zaufanie, jeśli znajduje się w globalnej pamięci podręcznej zestawów lub znajduje się w `fullTrustAssemblies` <xref:System.Security.Policy.StrongName> parametrze tablicy (). Do listy należy dodać tylko zestawy znane jako w pełni zaufane `fullTrustAssemblies` .  
  
 Przeciążenie ma następujący podpis:  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 Parametry <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> przeciążenia metody określają nazwę <xref:System.AppDomain> , dowód dla <xref:System.AppDomain> <xref:System.AppDomainSetup> obiektu, który identyfikuje bazę aplikacji dla piaskownicy, zestaw uprawnień do użycia i silne nazwy dla w pełni zaufanych zestawów.  
  
 Ze względów bezpieczeństwa baza aplikacji określona w `info` parametrze nie powinna być bazą aplikacji dla aplikacji hostingowych.  
  
 Dla `grantSet` parametru można określić zestaw uprawnień, który został utworzony jawnie, lub standardowy zestaw uprawnień utworzony przez <xref:System.Security.SecurityManager.GetStandardSandbox%2A> metodę.  
  
 W przeciwieństwie do większości <xref:System.AppDomain> obciążeń, dowód dla <xref:System.AppDomain> (który jest dostarczany przez `securityInfo` parametr) nie jest używany do określenia zestawu dotacji dla częściowo zaufanych zestawów. Zamiast tego jest on niezależnie określony przez `grantSet` parametr. Jednakże dowody mogą być używane do innych celów, takich jak określenie zakresu izolowanego magazynu.  
  
### <a name="to-run-an-application-in-a-sandbox"></a>Aby uruchomić aplikację w piaskownicy  
  
1. Utwórz zestaw uprawnień, który ma zostać udzielony dla niezaufanej aplikacji. Uprawnieniem minimalnym, które można udzielić <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> . Możesz również udzielić dodatkowych uprawnień, które mogą być bezpieczne dla niezaufanego kodu; na przykład <xref:System.Security.Permissions.IsolatedStorageFilePermission> . Poniższy kod tworzy nowy zestaw uprawnień z <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> uprawnieniami.  
  
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
  
     <xref:System.Security.SecurityManager.GetStandardSandbox%2A>Metoda zwraca `Internet` zestaw uprawnień lub `LocalIntranet` zestaw uprawnień w zależności od strefy w dowodu. <xref:System.Security.SecurityManager.GetStandardSandbox%2A>Ponadto konstruuje uprawnienia tożsamości dla niektórych obiektów dowodu, które przechodzą jako odwołania.  
  
2. Podpisz zestaw zawierający klasę hostingu (o nazwie `Sandboxer` w tym przykładzie), która wywołuje niezaufany kod. Dodaj <xref:System.Security.Policy.StrongName> użyty do podpisania zestawu do <xref:System.Security.Policy.StrongName> tablicy `fullTrustAssemblies` parametru <xref:System.AppDomain.CreateDomain%2A> wywołania. Klasa hostingu musi działać jako w pełni zaufana, aby umożliwić wykonywanie kodu częściowego zaufania lub oferowanie usług dla aplikacji częściowo zaufanej. Jest to sposób odczytywania <xref:System.Security.Policy.StrongName> zestawu:  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     Zestawy .NET Framework, takie jak mscorlib i System.dll, nie muszą być dodawane do listy całkowicie zaufanych, ponieważ są załadowane jako w pełni zaufane z globalnej pamięci podręcznej zestawów.  
  
3. Zainicjuj <xref:System.AppDomainSetup> parametr <xref:System.AppDomain.CreateDomain%2A> metody. Za pomocą tego parametru można kontrolować wiele ustawień nowego <xref:System.AppDomain> . <xref:System.AppDomainSetup.ApplicationBase%2A>Właściwość jest ważnym ustawieniem i powinna być inna niż <xref:System.AppDomainSetup.ApplicationBase%2A> Właściwość <xref:System.AppDomain> aplikacji hostingowej. Jeśli <xref:System.AppDomainSetup.ApplicationBase%2A> Ustawienia są takie same, aplikacja częściowej relacji zaufania może pobrać aplikację hostingu (jako w pełni zaufana), którą definiuje wyjątek, a tym samym ją wykorzystuje. Jest to kolejny powód, dla którego nie zaleca się przechwytywania (wyjątek). Ustawienie bazy aplikacji hosta różni się od bazy aplikacji w aplikacji w trybie piaskownicy, co zmniejsza ryzyko ataków wykorzystujących luki w zabezpieczeniach.  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. Wywołaj <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> Przeciążenie metody, aby utworzyć domenę aplikacji przy użyciu określonych parametrów.  
  
     Sygnaturą tej metody jest:  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     Informacje dodatkowe:  
  
    - Jest to jedyne Przeciążenie metody, <xref:System.AppDomain.CreateDomain%2A> która przyjmuje <xref:System.Security.PermissionSet> jako parametr, i w ten sposób jedynym przeciążeniem, które umożliwia załadowanie aplikacji w ustawieniu częściowej relacji zaufania.  
  
    - `evidence`Parametr nie jest używany do obliczania zestawu uprawnień; służy do identyfikacji przez inne funkcje .NET Framework.  
  
    - Ustawianie <xref:System.AppDomainSetup.ApplicationBase%2A> właściwości `info` parametru jest obowiązkowe dla tego przeciążenia.  
  
    - `fullTrustAssemblies`Parametr ma `params` słowo kluczowe, co oznacza, że nie jest konieczne tworzenie <xref:System.Security.Policy.StrongName> tablicy. Przekazanie wartości 0, 1 lub większej liczby silnych nazw jako parametrów jest dozwolone.  
  
    - Kod do utworzenia domeny aplikacji:  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. Załaduj kod w utworzonym obszarze piaskownicy <xref:System.AppDomain> . Można to zrobić na dwa sposoby:  
  
    - Wywołaj <xref:System.AppDomain.ExecuteAssembly%2A> metodę dla zestawu.  
  
    - Użyj <xref:System.Activator.CreateInstanceFrom%2A> metody, aby utworzyć wystąpienie klasy pochodnej z <xref:System.MarshalByRefObject> w nowym <xref:System.AppDomain> .  
  
     Druga metoda jest preferowana, ponieważ ułatwia przekazywanie parametrów do nowego <xref:System.AppDomain> wystąpienia. <xref:System.Activator.CreateInstanceFrom%2A>Metoda oferuje dwie ważne funkcje:  
  
    - Możesz użyć bazy kodu, która wskazuje lokalizację, która nie zawiera Twojego zestawu.  
  
    - Tworzenie można wykonać w obszarze <xref:System.Security.CodeAccessPermission.Assert%2A> dla pełnego zaufania ( <xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType> ), co umożliwia utworzenie wystąpienia klasy krytycznej. (Dzieje się tak, gdy zestaw nie ma znaczników przezroczystości i jest ładowany jako w pełni zaufany). W związku z tym należy zachować ostrożność, aby utworzyć tylko kod, który ufasz tej funkcji, i zalecamy utworzenie tylko wystąpień w pełni zaufanych klas w nowej domenie aplikacji.  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     Aby utworzyć wystąpienie klasy w nowej domenie, Klasa musi być rozszerzona o <xref:System.MarshalByRefObject> klasę.
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. Odpakuj nowe wystąpienie domeny do odwołania w tej domenie. To odwołanie służy do wykonywania niezaufanego kodu.  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. Wywołaj `ExecuteUntrustedCode` metodę w wystąpieniu `Sandboxer` klasy, która właśnie została utworzona.  
  
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
  
     <xref:System.Reflection>służy do pobierania dojścia metody z częściowo zaufanego zestawu. Uchwyt może służyć do wykonywania kodu w bezpieczny sposób z minimalnymi uprawnieniami.  
  
     Przed przystąpieniem do drukowania w poprzednim kodzie należy zwrócić uwagę <xref:System.Security.PermissionSet.Assert%2A> na uprawnienia pełnego zaufania <xref:System.Security.SecurityException> .  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     Potwierdzenie pełnego zaufania służy do uzyskiwania rozszerzonych informacji z <xref:System.Security.SecurityException> . Bez <xref:System.Security.PermissionSet.Assert%2A> , <xref:System.Security.SecurityException.ToString%2A> Metoda <xref:System.Security.SecurityException> wykryje, że na stosie znajduje się częściowo zaufany kod i ograniczy zwrócone informacje. Może to spowodować problemy z bezpieczeństwem, jeśli kod częściowego zaufania może odczytać te informacje, ale ryzyko to nie jest udzielane <xref:System.Security.Permissions.UIPermission> . Potwierdzenie pełnego zaufania powinno być używane oszczędnie i tylko wtedy, gdy masz pewność, że nie zezwolisz na podniesienie poziomu kodu zaufania do pełnego zaufania. Zgodnie z regułą nie należy wywoływać kodu, który nie jest zaufany w tej samej funkcji, i po wywołaniu potwierdzenia pełnego zaufania. Dobrym sposobem jest zawsze przywrócenie potwierdzenia po zakończeniu korzystania z niego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład implementuje procedurę opisaną w poprzedniej sekcji. W przykładzie projekt o nazwie `Sandboxer` w rozwiązaniu programu Visual Studio zawiera również projekt o nazwie `UntrustedCode` , który implementuje klasę `UntrustedClass` . W tym scenariuszu przyjęto założenie, że pobrano zestaw biblioteczny zawierający metodę, która powinna zostać zwrócona, `true` lub `false` Aby wskazać, czy podany numer jest numerem Fibonacci. Zamiast tego Metoda próbuje odczytać plik z komputera. Poniższy przykład pokazuje kod niezaufany.  
  
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
  
 Poniższy przykład pokazuje `Sandboxer` kod aplikacji, który wykonuje kod niezaufany.  
  
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
