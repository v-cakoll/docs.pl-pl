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
ms.openlocfilehash: 92e49af78d42f360d5798a72d4e7b981295947e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181102"
---
# <a name="using-the-assert-method"></a>Korzystanie z metody Assert
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A>jest metodą, która może być wywoływana <xref:System.Security.PermissionSet> na klasy uprawnień dostępu do kodu i klasy. Można użyć **Assert,** aby włączyć kod (i podrzędnych wywołań) do wykonywania akcji, które kod ma uprawnienia do zrobienia, ale jego wywołujących może nie mieć uprawnień do zrobienia. Asercja zabezpieczeń zmienia normalny proces, który środowisko wykonawcze wykonuje podczas sprawdzania zabezpieczeń. Gdy dochodzisz uprawnienia, informuje system zabezpieczeń, aby nie sprawdzać wywołań kodu dla potwierdzonych uprawnień.  
  
> [!CAUTION]
> Używaj potwierdzeń ostrożnie, ponieważ mogą one otworzyć luki w zabezpieczeniach i podważyć mechanizm wykonywania ograniczeń zabezpieczeń.  
  
 Potwierdzenia są przydatne w sytuacjach, w których biblioteka wywołuje do kodu niezarządzanego lub wywołuje, który wymaga uprawnienia, które nie jest oczywiście związane z zamierzonego użycia biblioteki. Na przykład cały kod zarządzany, który wywołuje do kodu niezarządzanego musi mieć **SecurityPermission** z **UnmanagedCode** flagi określone. Kod, który nie pochodzi z komputera lokalnego, na przykład kod pobrany z lokalnego intranetu, nie zostanie domyślnie przyznany temu uprawnieniu. W związku z tym w celu kodu, który jest pobierany z lokalnego intranetu, aby móc wywołać bibliotekę, która używa kodu niezarządzanego, musi mieć uprawnienia potwierdzone przez bibliotekę. Ponadto niektóre biblioteki mogą wykonywać wywołania, które są niewidoczne dla osób wywołujących i wymagają specjalnych uprawnień.  
  
 Można również użyć potwierdzeń w sytuacjach, w których kod uzyskuje dostęp do zasobu w sposób, który jest całkowicie ukryty przed obiektami wywołującymi. Załóżmy na przykład, że biblioteka uzyskuje informacje z bazy danych, ale w procesie odczytuje również informacje z rejestru komputera. Ponieważ deweloperzy korzystający z biblioteki nie mają dostępu do źródła, nie mają możliwości poznania, że ich kod wymaga **RegistryPermission** w celu użycia kodu. W takim przypadku, jeśli zdecydujesz, że nie jest uzasadnione lub konieczne, aby wymagać, aby osoby wywołujące kodu mają uprawnienia dostępu do rejestru, można dochodzić uprawnień do odczytu rejestru. W tej sytuacji jest właściwe dla biblioteki do potwierdzenia uprawnienia, tak aby wywołania bez **RegistryPermission** można użyć biblioteki.  
  
 Twierdzenie wpływa na spacer stosu tylko wtedy, gdy potwierdzone uprawnienie i uprawnienie wymagane przez wywołującego podrzędnego są tego samego typu i jeśli wymagane uprawnienie jest podzbiorem potwierdzonego uprawnienia. Na przykład jeśli potwierdzić **FileIOPermission** do odczytu wszystkich plików na dysku C i podrzędne żądanie jest dla **FileIOPermission** do odczytu plików w C:\Temp, twierdzenie może mieć wpływ na spacer stosu; jednak jeśli żądanie było **fileiopermission** do zapisu na dysku C, twierdzenie nie miałoby wpływu.  
  
 Aby wykonać potwierdzenia, kod musi być przyznane zarówno uprawnienia, <xref:System.Security.Permissions.SecurityPermission> które są twierdząc i który reprezentuje prawo do potwierdzeń. Chociaż można potwierdzić uprawnienia, które kod nie został przyznany, twierdzenie byłoby bezcelowe, ponieważ sprawdzanie zabezpieczeń zakończy się niepowodzeniem, zanim twierdzenie może spowodować jego powodowie.  
  
 Na poniższej ilustracji przedstawiono, co się dzieje, gdy używasz **Assert**. Załóżmy, że następujące instrukcje są prawdziwe dotyczące zestawów A, B, C, E i F i dwa uprawnienia, P1 i P1A:  
  
- P1A reprezentuje prawo do odczytu plików .txt na dysku C.  
  
- P1 reprezentuje prawo do odczytu wszystkich plików na dysku C.  
  
- P1A i P1 są typami **FileIOPermission,** a P1A jest podzbiorem P1.  
  
- Zestawy E i F otrzymały uprawnienie P1A.  
  
- Zestaw C otrzymał uprawnienie P1.  
  
- Zestawy A i B nie zostały przyznane ani P1, ani P1A uprawnień.  
  
- Metoda A jest zawarta w zestawie A, metoda B jest zawarta w zestawie B i tak dalej.  
  
 ![Diagram, który pokazuje Assert zestawy metody.](./media/using-the-assert-method/assert-method-assemblies.gif)
  
 W tym scenariuszu metoda A wywołuje B, B wywołuje C, C wywołuje E i E wywołuje F. Metoda C potwierdza uprawnienia do odczytu plików na dysku C (uprawnienie P1), a metoda E wymaga uprawnień do odczytu plików .txt na dysku C (uprawnienie P1A). Gdy żądanie w F zostanie napotkane w czasie wykonywania, spacer stosu jest wykonywane, aby sprawdzić uprawnienia wszystkich wywołujących F, począwszy od E. E otrzymał uprawnienia P1A, więc stos przejść przechodzi do zbadania uprawnień C, gdzie twierdzenie C jest odnaleziony. Ponieważ żądane uprawnienie (P1A) jest podzbiorem potwierdzonego uprawnienia (P1), przejście stosu zatrzymuje się, a sprawdzanie zabezpieczeń zostanie automatycznie pomyślnie. Nie ma znaczenia, że zestawy A i B nie otrzymały uprawnień P1A. Potwierdzając P1, metoda C zapewnia, że jego wywołujących można uzyskać dostęp do zasobu chronionego przez P1, nawet jeśli wywołujących nie zostały przyznane uprawnienia dostępu do tego zasobu.  
  
 Jeśli projektujesz bibliotekę klas i klasa uzyskuje dostęp do chronionego zasobu, w większości przypadków należy wysilić żądanie zabezpieczeń wymagające, aby osoby wywołujące klasy miały odpowiednie uprawnienia. Jeśli klasa następnie wykonuje operację, dla której wiadomo, że większość jego wywołujących nie będzie miał uprawnień, a jeśli chcesz wziąć odpowiedzialność za umożliwienie tych wywołujących wywołać kod, można potwierdzić uprawnienia wywołując **Assert** metody na obiekt uprawnień, który reprezentuje operację, którą wykonuje kod. Za pomocą **Assert** w ten sposób umożliwia wywołujących, które normalnie nie można tego zrobić, więc wywołać kod. W związku z tym jeśli potwierdzisz uprawnienie, należy upewnić się, że należy wykonać odpowiednie kontrole zabezpieczeń wcześniej, aby zapobiec niewłaściwie składnika.  
  
 Załóżmy na przykład, że klasa biblioteki jest wysoce zaufana, która usuwa pliki. Uzyskuje dostęp do pliku, wywołując niezarządzaną funkcję Win32. Wywołujący wywołuje metodę **delete** kodu, przekazując w nazwie pliku do usunięcia, C:\Test.txt. W ramach **Metody Delete** kod <xref:System.Security.Permissions.FileIOPermission> tworzy obiekt reprezentujący dostęp do zapisu do C:\Test.txt. (Aby usunąć plik, wymagany jest dostęp do zapisu). Kod następnie wywołuje imperatywnych kontroli zabezpieczeń, wywołując **FileIOPermission** obiektu **Demand** metody. Jeśli jeden z wywołujących w stosie wywołań <xref:System.Security.SecurityException> nie ma tego uprawnienia, a jest generowany. Jeśli nie zostanie zgłoszony wyjątek, wiesz, że wszystkie obiekty wywołujące mają prawo dostępu do C:\Test.txt. Ponieważ uważasz, że większość obiektów wywołujących nie będzie miał uprawnień dostępu <xref:System.Security.Permissions.SecurityPermission> do kodu niezarządzanego, kod następnie tworzy obiekt, który reprezentuje prawo do wywołania kodu niezarządzanego i wywołuje właściwego **Assert** metody. Na koniec wywołuje niezarządzaną funkcję Win32, aby usunąć C:\Text.txt i zwraca kontrolę do wywołującego.  
  
> [!CAUTION]
> Należy upewnić się, że kod nie używa potwierdzeń w sytuacjach, gdy kod może być używany przez inny kod, aby uzyskać dostęp do zasobu, który jest chroniony przez uprawnienie, które potwierdzasz. Na przykład w kodzie, który zapisuje do pliku, którego nazwa jest określona przez wywołującego jako parametr, nie można potwierdzić **FileIOPermission** do zapisywania do plików, ponieważ kod będzie otwarty do niewłaściwego użycia przez osobę trzecią.  
  
 Podczas korzystania ze składni zabezpieczeń imperatywów wywołanie **Assert** metody na wiele uprawnień w tej samej metodzie powoduje wyjątek zabezpieczeń do zaliczenia. Zamiast tego należy utworzyć **Obiekt PermissionSet,** przekazać go poszczególnych uprawnień, które chcesz wywołać, a następnie **wywołać Assert** metody na **PermissionSet** obiektu. Assert można **wywołać Assert** metody więcej niż jeden raz, gdy używasz składni zabezpieczeń deklaratywne.  
  
 Poniższy przykład przedstawia składnię deklaratywną do zastępowania kontroli zabezpieczeń przy użyciu **Assert** metody. Należy zauważyć, że **FileIOPermissionAttribute** składni <xref:System.Security.Permissions.SecurityAction> ma dwie wartości: wyliczenie i lokalizacji pliku lub katalogu, do którego ma być przyznane uprawnienie. Wywołanie **Assert** powoduje żądania dostępu `C:\Log.txt` do pomyślnego, mimo że wywołujący nie są sprawdzane pod kątem uprawnień dostępu do pliku.  
  
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
  
 Następujące fragmenty kodu pokazują niezbędną składnię zastępowania kontroli zabezpieczeń przy użyciu **Assert** metody. W tym przykładzie jest deklarowane wystąpienie obiektu **FileIOPermission.** Jego konstruktor jest przekazywany **FileIOPermissionAccess.AllAccess** do definiowania typu dozwolonego dostępu, a następnie ciąg opisujący lokalizację pliku. Po zdefiniowaniu **FileIOPermission** obiekt, wystarczy wywołać jego **Assert** metody, aby zastąpić sprawdzanie zabezpieczeń.  
  
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

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.SecurityPermission>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.Permissions.SecurityAction>
- [Atrybuty](../../standard/attributes/index.md)
- [Zabezpieczenia dostępu kodu](code-access-security.md)
