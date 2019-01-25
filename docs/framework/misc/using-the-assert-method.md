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
ms.openlocfilehash: 31dcaeb6d3adcd658a9844ae5cf8e758172bd7bc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516518"
---
# <a name="using-the-assert-method"></a>Korzystanie z metody Assert
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A> jest to metoda może być wywoływana w klasach uprawnienia dostępu kodu i na <xref:System.Security.PermissionSet> klasy. Możesz użyć **Asercja** aby umożliwić kod (i wywoływania podrzędnego) do wykonania akcji, które Twój kod ma uprawnienie do wykonywania, ale wywołujące może nie masz uprawnienia do wykonania. Potwierdzenie zabezpieczeń zmienia normalnego procesu, jak środowisko uruchomieniowe wykonuje podczas sprawdzania zabezpieczeń. Uprawnienie jest assert, informuje o system zabezpieczeń nie, aby sprawdzić obiektów wywołujących swój kod pod kątem potwierdzone uprawnienia.  
  
> [!CAUTION]
>  Używać asercji ostrożnie, ponieważ mogą otworzyć luk w zabezpieczeniach i podważać mechanizmu wymuszania ograniczeń zabezpieczeń w środowisku uruchomieniowym.  
  
 Potwierdzenia są przydatne w sytuacjach, w których bibliotekę wywołuje kod niezarządzany lub sprawia, że wywołanie, które wymaga uprawnień, które oczywiście nie jest powiązana z zamierzonym użyciem bibliotek. Na przykład, wszystkie zarządzane kod, który wywołuje kod niezarządzany musi mieć **SecurityPermission** z **UnmanagedCode** określono flagę. Kod, który nie pochodzi z komputera lokalnego, takie jak kod, który jest pobierany z lokalny intranet, nie otrzyma tego uprawnienia domyślnie. W związku z tym aby kod, który jest pobierany z lokalny intranet, aby można było wywołać bibliotekę, która korzysta z kodu niezarządzanego, musi mieć uprawnienie potwierdzone przez bibliotekę. Ponadto niektóre biblioteki może wykonywać wywołania, są niewidoczne dla kodu wywołującego, które wymagają specjalnych uprawnień.  
  
 Umożliwia także potwierdzenia w sytuacjach, w których kod uzyskuje dostęp do zasobów w sposób, który jest całkowicie ukryte z wywołującym. Na przykład załóżmy, że Twoja biblioteka uzyskuje informacje z bazy danych, ale w procesie również odczytuje informacje z rejestru komputera. Ponieważ deweloperzy korzystający z biblioteki nie mają dostępu do źródła, nie mają żadnej możliwość określenia, czy ich kod wymaga **RegistryPermission** aby można było używać kodu. W tym przypadku Jeśli zdecydujesz, że nie jest uzasadnione i konieczne wymagają wywoływania w kodzie miał uprawnienia do dostępu do rejestru, możesz assert uprawnień do odczytywania z rejestru. W tej sytuacji jest odpowiednie dla biblioteki do potwierdzenia zgody, tak że obiekty wywołujące, bez **RegistryPermission** biblioteki można używać.  
  
 Potwierdzenie wpływa na przejście przez stos tylko wtedy, gdy jest to potwierdzone uprawnienia i uprawnienia wymagane przez obiekt wywołujący podrzędne są tego samego typu, a Jeśli żądane uprawnienie jest podzbiorem potwierdzone uprawnienia. Na przykład, jeśli użytkownik asercja **FileIOPermission** można odczytać wszystkich plików na dysku C, a żądanie podrzędne wykonywane **FileIOPermission** odczytywać pliki w C:\Temp, potwierdzenie mogą mieć wpływ na stosów; Jednakże jeśli żądanie dotyczyło **FileIOPermission** do zapisu na dysku C, potwierdzenie miałaby żadnego efektu.  
  
 Aby wykonać potwierdzenia, kod musi otrzymać uprawnienia są potwierdzające i <xref:System.Security.Permissions.SecurityPermission> reprezentujący prawo do wprowadzania potwierdzenia. Mimo że można assert uprawnienia, które nie udzielono kodu i potwierdzenie byłaby sensu, ponieważ kontrola zabezpieczeń może zakończyć się niepowodzeniem, zanim potwierdzenie może spowodować, że powiodło się.  
  
 Na poniższej ilustracji przedstawiono, co się stanie, gdy używasz **Asercja**. Załóżmy, że następujące instrukcje są spełnione dotyczące zestawów A, B, C, E i f. i uprawnienia P1 i P1A:  
  
-   P1A reprezentuje uprawnienie do odczytu plików txt na dysku C.  
  
-   P1 reprezentuje uprawnienie do odczytu wszystkich plików na dysku C.  
  
-   To P1 i P1A **FileIOPermission** typów i P1A jest podzbiorem P1.  
  
-   Zestawy E i f. przyznano uprawnienie P1A.  
  
-   Zestaw C ma uprawnienia P1.  
  
-   Zestawy, A i B ma odpowiednie uprawnienia P1A ani P1.  
  
-   Metoda A znajduje się w zestawie A, metoda B jest zawarty w zestawie B i tak dalej.  
  
 ![](../../../docs/framework/misc/media/assert.gif "Assert")  
Za pomocą potwierdzeń  
  
 W tym scenariuszu, metoda A wywołuje usługę B, wywołania B, C, wywołania C E, wywołania E F. Metoda C potwierdza uprawnienie do odczytania plików na dysku C (uprawnienie P1) i metody E żądania uprawnień do odczytu plików txt na dysku C (uprawnienie P1A). Po napotkaniu w czasie wykonywania żądanie w F przeszukiwania stosu jest wykonywane, aby sprawdzić uprawnienia wszystkich obiektów wywołujących f, począwszy od E. E ma uprawnienia P1A, więc przeszukiwania stosu przechodzi do sprawdzania uprawnień C, gdzie odnaleziono potwierdzenia C. Ponieważ żądane uprawnienia (P1A) jest podzbiorem potwierdzone uprawnienia (P1), zatrzymanie przeszukiwania stosu i sprawdzanie zabezpieczeń automatycznie zakończy się pomyślnie. Nie ma znaczenia w tym zestawów, które A i B nie przyznano uprawnień P1A. Potwierdzanie P1, Metoda C zapewnia wywołujące dostęp zasobów chronionych przez P1, nawet wtedy, gdy funkcja wywołująca nie przyznano uprawnień dostępu do tego zasobu.  
  
 Jeśli projekt biblioteki klas, klasa uzyskuje dostęp do chronionego zasobu w większości przypadków należy żądania zabezpieczeń wymaga, że funkcja wywołująca klasy mają odpowiednie uprawnienia. Jeśli klasy następnie wykonuje operację na, którym wiadomo, większość wywołujące nie będziesz mieć uprawnienia, a jeśli pragnących odpowiedzialność umożliwiając te obiekty wywołujące wywołać kod można assert uprawnienia, wywołując **Asercja** metody na obiekt uprawnień, który reprezentuje operację wykonywania kodu. Za pomocą **Asercja** w ten sposób umożliwia wywołań, w których zwykle nie może wykonać to wywołanie kodu. W związku z tym jeśli uprawnienie jest assert, należy koniecznie kontrole zabezpieczeń odpowiednich wcześniej aby zapobiec niewłaściwemu składnika.  
  
 Na przykład załóżmy, że klasa wysoce zaufanym biblioteka ma metodę, która usuwa pliki. Plik uzyskuje dostęp przez wywołanie funkcji Win32 niezarządzanej. Obiekt wywołujący wywołuje kodu **Usuń** metodę przekazywania pliku, który zostanie usunięty, C:\Test.txt. W ramach **Usuń** tworzy kodzie metody <xref:System.Security.Permissions.FileIOPermission> obiekt reprezentujący C:\Test.txt dostęp do zapisu. (Dostęp do zapisu jest wymagane do usunięcia pliku). Następnie kod wywołuje imperatywne sprawdzanie zabezpieczeń, wywołując **FileIOPermission** obiektu **żądanie** metody. Jeśli jeden z obiektów wywołujących w stosie wywołań nie ma to uprawnienie <xref:System.Security.SecurityException> zgłaszany. Jeśli jest zgłaszany żaden wyjątek, wiesz, że wszystkie obiekty wywołujące mają prawa dostępu C:\Test.txt. Ponieważ uważasz, że większość wywołań usługi nie ma uprawnienia do dostępu do kodu niezarządzanego, kodzie następnie tworzy <xref:System.Security.Permissions.SecurityPermission> obiekt, który reprezentuje po prawej stronie, aby wywoływać kod niezarządzany, a następnie wywołuje obiekt **Asercja** metody. Na koniec wywołuje funkcję Win32 niezarządzanych w celu usunięcia C:\Text.txt i przekazuje sterowanie do obiektu wywołującego.  
  
> [!CAUTION]
>  Należy upewnić się, że Twój kod nie potwierdzenia w sytuacjach, w którym kod może służyć przez inny kod dostępu do zasobu, który jest chroniony przez uprawnienia, które są potwierdzające. Na przykład w kodzie, który zapisuje dane w pliku, którego nazwa jest określona przez obiekt wywołujący, jako parametr, użytkownik będzie nie asercja **FileIOPermission** do zapisu do plików, ponieważ kod jest otwarte nieuprawnione użycie przez inną firmę.  
  
 Gdy używasz składnia zabezpieczeń imperatywnych, wywołanie **Asercja** metody na wiele uprawnień w tej samej metody powoduje, że zostanie wygenerowany wyjątek zabezpieczeń. Zamiast tego należy utworzyć **PermissionSet** obiektów, przekazać go indywidualne uprawnienia, które chcesz wywołać, a następnie wywołaj **Asercja** metody **PermissionSet** obiekt. Możesz wywołać **Asercja** metoda więcej niż jeden raz na zastosowania składnia zabezpieczeń deklaratywnych.  
  
 W poniższym przykładzie pokazano składni deklaratywnej dla bezpieczeństwa, który umożliwia sprawdzenie za pomocą **Asercja** metody. Należy zauważyć, że **FileIOPermissionAttribute** składni przyjmuje dwie wartości: <xref:System.Security.Permissions.SecurityAction> wyliczenie i lokalizację pliku lub katalogu, do którego ma zostać udzielone uprawnienia. Wywołanie **Asercja** powoduje, że żądania w celu uzyskania dostępu do `C:\Log.txt` została wykonana pomyślnie, nawet jeśli obiekty wywołujące nie są sprawdzane pod kątem uprawnienia dostępu do tego pliku.  
  
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
  
 Poniższe fragmenty kodu pokazują składnia imperatywna, dla bezpieczeństwa, który umożliwia sprawdzenie za pomocą **Asercja** metody. W tym przykładzie wystąpienie **FileIOPermission** obiekt nie został zadeklarowany. Jego konstruktor jest przekazywany **FileIOPermissionAccess.AllAccess** zdefiniować typ dostępu przyznany, następuje ciąg opisujący lokalizację pliku. Raz **FileIOPermission** obiekt jest zdefiniowany, musisz wywołać jej **Asercja** metody do przesłonięcia sprawdzanie zabezpieczeń.  
  
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
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.SecurityPermission>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.Permissions.SecurityAction>
- [Atrybuty](../../../docs/standard/attributes/index.md)
- [Zabezpieczenia dostępu kodu](../../../docs/framework/misc/code-access-security.md)
