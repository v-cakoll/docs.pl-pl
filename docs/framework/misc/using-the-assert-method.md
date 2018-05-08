---
title: Korzystanie z metody Assert
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- granting permissions, overriding security checks
- code access security, overriding security checks
- overriding security checks
- security [.NET Framework], overriding security checks
- security [.NET Framework], assertions
- asserted permissions
- Assert method
- caller security checks
- permissions [.NET Framework], overriding security checks
- permissions [.NET Framework], assertions
ms.assetid: 1e40f4d3-fb7d-4f19-b334-b6076d469ea9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ea8be23eb6fd2500e59527890b874b8f19ec06d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-the-assert-method"></a>Korzystanie z metody Assert
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A> jest to metoda może być wywoływana dla klasy uprawnień dostępu kodu i na <xref:System.Security.PermissionSet> klasy. Można użyć **Assert** Aby włączyć kod (i wywoływania podrzędnego) do wykonywania akcji, które kod ma uprawnienie do wykonywania, ale jego wywołań może nie mieć odpowiednich uprawnień. Potwierdzenia zabezpieczeń zmienia normalny proces, który wykonuje środowiska uruchomieniowego podczas sprawdzania zabezpieczeń. Jeśli Potwierdzaj uprawnienia, informuje system zabezpieczeń nie, aby sprawdzić wywołań kodu potwierdzone uprawnienia.  
  
> [!CAUTION]
>  Ostrożnie korzystaj potwierdzeń, ponieważ mogą otworzyć luk w zabezpieczeniach i obniżyć środowiska uruchomieniowego mechanizmu wymuszania ograniczeń zabezpieczeń.  
  
 Potwierdzenia są przydatne w sytuacjach, w których biblioteki wywołania do kodu niezarządzanego lub nawiązuje połączenie, które wymaga uprawnień, które oczywiście nie jest powiązana z zamierzonym użyciem biblioteki. Na przykład wszystkie zarządzane kod, który musi mieć wywołania do kodu niezarządzanego **SecurityPermission** z **UnmanagedCode** określona flaga. Kod, który nie pochodzi z komputera lokalnego, takie jak kod, który jest pobierana z lokalny intranet, zostanie nie można przyznać uprawnienia domyślne. W związku z tym aby kod, który jest pobierana z lokalny intranet, aby można było wywołać biblioteki, która korzysta z kodu niezarządzanego, musi mieć uprawnienie potwierdzone przez bibliotekę. Ponadto niektóre biblioteki może uniemożliwić wywołania są niewidoczne dla kodu wywołującego, które wymagają szczególnych uprawnień.  
  
 Umożliwia także potwierdzenia w sytuacjach, w których kod uzyskuje dostęp do zasobów w taki sposób, który jest całkowicie ukryty z wywołań. Na przykład załóżmy, że biblioteka uzyskuje informacje z bazy danych, ale w procesie również odczytuje informacje z rejestru komputera. Ponieważ deweloperów korzystających z biblioteki nie ma dostępu do źródła, ich nie ma możliwości wiedząc, że ich kod wymaga **RegistryPermission** aby można było używać kodu. Jeśli zdecydujesz, że nie jest uzasadnione lub trzeba mieć wywołań kodu uprawnień dostępu do rejestru, można w takim przypadku assert uprawnień do odczytywania rejestru. W takiej sytuacji jest odpowiednie dla biblioteki do potwierdzenia uprawnienia, tak że wywołań bez **RegistryPermission** biblioteki można używać.  
  
 Potwierdzenie dotyczy przeszukiwania stosu tylko wtedy, gdy potwierdzone uprawnienia i wymagane przez obiekt wywołujący podrzędne są tego samego typu i Jeśli żądane uprawnienie jest podzbiorem potwierdzone uprawnienia. Na przykład, jeśli użytkownik assert **FileIOPermission** do odczytu wszystkich plików na dysku C, a żądanie podrzędne wykonywane **FileIOPermission** odczytywać pliki w C:\Temp, potwierdzenie mogą wpłynąć na przeszukiwania stosu; Jednak jeśli żądanie dotyczyło **FileIOPermission** zapisu na dysku C, potwierdzenie czy nie obowiązują.  
  
 Aby wykonać potwierdzeń, kodu musi otrzymać uprawnienia są zostanie i <xref:System.Security.Permissions.SecurityPermission> reprezentujący prawo do wprowadzania potwierdzenia. Mimo że można assert uprawnienia, które nie zostało udzielone kodu, potwierdzenie byłoby bezcelowe, ponieważ kontrola zabezpieczeń nie powiedzie się przed potwierdzenia może spowodować, że plik powiodło się.  
  
 Na poniższej ilustracji pokazano, co się dzieje, gdy używasz **Assert**. Załóżmy, że następujące instrukcje są spełnione dotyczące zestawów A, B, C, E i F i uprawnienia P1 i P1A:  
  
-   P1A reprezentuje prawo do odczytu dla plików txt na dysku C.  
  
-   P1 reprezentuje prawo do odczytu wszystkich plików na dysku C.  
  
-   P1A i P1 są **FileIOPermission** typy i P1A jest podzbiorem P1.  
  
-   Zestawy E i F przyznano uprawnienia P1A.  
  
-   Zestaw C ma uprawnienia P1.  
  
-   Zestawy, A i B ma odpowiednie uprawnienia P1 ani P1A.  
  
-   Metoda jest zawarty w zestawie A, metoda B jest zawarty w zestawie B i tak dalej.  
  
 ![](../../../docs/framework/misc/media/assert.gif "Assert")  
Przy użyciu Assert  
  
 W tym scenariuszu, wywołania metody A B, wywołania B C, wywołania C E i E wywołania F. Metoda C potwierdza uprawnień do odczytu plików na dysku C (uprawnienia P1), a metoda E żądania uprawnień do odczytu plików txt na dysku C (uprawnienie P1A). Po napotkaniu popyt F w czasie wykonywania przeszukiwania stosu jest wykonywane, aby sprawdzić uprawnienia wszystkim zainteresowanym F, począwszy od E. E ma uprawnienia P1A, więc przeszukiwania stosu będzie kontynuowana, aby sprawdzić uprawnienia C, gdy zostanie wykryta potwierdzenia C. Ponieważ żądane uprawnienie (P1A) jest podzbiorem potwierdzone uprawnienia (P1), zatrzymuje przeszukiwania stosu i sprawdzania zabezpieczeń automatycznie zakończy się pomyślnie. Nie ma znaczenia, że zestawy, które A i B nie udzielono uprawnienia P1A. Przez potwierdzające P1, Metoda C zapewnia, że elementy wywołujące pod można dostęp do zasobów chronionych przez P1, nawet jeśli wywołań nie przyznano uprawnień dostępu do tego zasobu.  
  
 Jeśli projektu biblioteki klas, klas uzyskuje dostęp do chronionych zasobów w większości przypadków należy żądania zabezpieczeń wymagających, że obiekty wywołujące klasy mają odpowiednie uprawnienia. Jeśli klasa wykonuje następnie wykonanie operacji, które znasz większość elementy wywołujące pod nie będzie mieć uprawnień, a jeśli pragnących odpowiedzialność za umożliwienie tych wywołań wywołań kodu, można assert uprawnienia, wywołując **Assert** metody dla obiektu uprawnień, reprezentujący operację wykonywania kodu. Przy użyciu **Assert** w ten sposób umożliwia wywołań, które normalnie nie może wykonać tego wywołania kodu. W związku z tym jeśli Potwierdzaj uprawnienia, należy koniecznie sprawdzania odpowiednich zabezpieczeń wcześniej aby zapobiec niewłaściwemu składnika.  
  
 Na przykład załóżmy, że klasa wysoce zaufanych biblioteka ma metodę, która usuwa pliki. Uzyskuje dostęp do pliku przez wywołanie funkcji niezarządzanej Win32. Obiekt wywołujący wywołuje swój kod **usunąć** metoda przekazywania pliku, który zostanie usunięty, C:\Test.txt. W ramach **usunąć** tworzy kod metody <xref:System.Security.Permissions.FileIOPermission> obiekt reprezentujący C:\Test.txt dostęp do zapisu. (Dostęp do zapisu jest wymagany do usunięcia pliku). Następnie kod wywołuje wyboru zabezpieczenia imperatywne przez wywołanie metody **FileIOPermission** obiektu **żądanie** metody. Jeśli jeden z obiektów wywołujących na stosie wywołań nie ma to uprawnienie <xref:System.Security.SecurityException> jest generowany. Jeśli żaden wyjątek jest zgłaszany, wiadomo, że wszystkim zainteresowanym mają prawa dostępu C:\Test.txt. Ponieważ uważasz, że większość z wywołań nie będzie mieć uprawnień dostęp do kodu niezarządzanego, następnie tworzy kod <xref:System.Security.Permissions.SecurityPermission> obiekt, który reprezentuje prawo do wywoływanie kodu niezarządzanego i wywołuje metodę obiektu **Assert** metody. Na koniec wywołania funkcji niezarządzanej Win32, aby usunąć C:\Text.txt i zwraca sterowania do obiektu wywołującego.  
  
> [!CAUTION]
>  Należy upewnić się, że kod nie używa potwierdzenia w sytuacjach, gdy Twoje kod może być używany przez inny kod dostępu do zasobu, która jest chroniona przez uprawnienia, które są zostanie. Na przykład w kodzie, który zapisuje do pliku, którego nazwa jest określona przez obiekt wywołujący jako parametru, użytkownik może nie assert **FileIOPermission** do zapisu do plików, ponieważ kod jest otwarte nieprawidłowego użycia przez inną firmę.  
  
 Gdy używasz składni zabezpieczenia imperatywne wywoływania **Assert** metody na wiele uprawnień w tej samej metody powoduje, że zostanie wygenerowany wyjątek zabezpieczeń. Zamiast tego należy utworzyć **PermissionSet** obiektów, przekazywanie ich indywidualnych uprawnień, aby wywołać, a następnie wywołać **Assert** metoda **PermissionSet** obiekt. Możesz wywołać **Assert** więcej niż jeden raz po użyj składni zabezpieczenia deklaratywne metody.  
  
 W poniższym przykładzie przedstawiono składni deklaratywnej kontroli bezpieczeństwa przy użyciu **Assert** metody. Zwróć uwagę, że **FileIOPermissionAttribute** składni ma dwie wartości: <xref:System.Security.Permissions.SecurityAction> wyliczenie i lokalizację pliku lub katalogu, do której ma zostać udzielone uprawnienia. Wywołanie **Assert** powoduje, że żądania dostępu do `C:\Log.txt` zakończyła się powodzeniem, nawet jeśli wywołań nie są sprawdzane pod kątem uprawnienia dostępu do tego pliku.  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
  
      End Sub  
  
     <FileIOPermission(SecurityAction.Assert, All := "C:\Log.txt")> Public Sub   
      MakeLog()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now) '  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {      
      }     
      [FileIOPermission(SecurityAction.Assert, All = @"C:\Log.txt")]  
      public void MakeLog()  
      {     
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}   
```  
  
 Poniższe fragmenty kodu Pokaż składni konieczne kontroli bezpieczeństwa przy użyciu **Assert** metody. W tym przykładzie wystąpienia **FileIOPermission** jest zadeklarowany jako obiekt. Jego konstruktor jest przekazywany **FileIOPermissionAccess.AllAccess** do definiowania typu dostępu dozwolone, a następnie ciąg opisujący lokalizacji pliku. Raz **FileIOPermission** obiektu jest zdefiniowana, należy wywołać jej **Assert** metody do przesłonięcia sprawdzanie zabezpieczeń.  
  
```vb  
Option Explicit  
Option Strict  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
      End Sub 'New  
  
      Public Sub MakeLog()  
         Dim FilePermission As New FileIOPermission(FileIOPermissionAccess.AllAccess, "C:\Log.txt")  
         FilePermission.Assert()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now)  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {      
      }     
      public void MakeLog()  
      {  
         FileIOPermission FilePermission = new FileIOPermission(FileIOPermissionAccess.AllAccess,@"C:\Log.txt");   
         FilePermission.Assert();  
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.PermissionSet>  
 <xref:System.Security.Permissions.SecurityPermission>  
 <xref:System.Security.Permissions.FileIOPermission>  
 <xref:System.Security.Permissions.SecurityAction>  
 [Atrybuty](../../../docs/standard/attributes/index.md)  
 [Zabezpieczenia dostępu kodu](../../../docs/framework/misc/code-access-security.md)
