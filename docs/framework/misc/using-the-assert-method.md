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
ms.openlocfilehash: f43ba2963ec447e5193da73452537b2539c51857
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206036"
---
# <a name="using-the-assert-method"></a>Korzystanie z metody Assert
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A>to metoda, która może być wywoływana dla klas uprawnień dostępu kodu i <xref:System.Security.PermissionSet> klasy. Za pomocą potwierdzeń można włączyć kod (i obiekty podrzędne wywołujące), aby wykonać akcje, do których Twój kod ma uprawnienia, ale jego obiekty wywołujące mogą nie mieć uprawnień do wykonania. Potwierdzenie zabezpieczeń zmienia normalny proces wykonywany przez środowisko uruchomieniowe podczas sprawdzania zabezpieczeń. Po podaniu uprawnienia Nakazuje systemowi zabezpieczeń, aby nie sprawdzać obiektów wywołujących kod dla potwierdzonego uprawnienia.  
  
> [!CAUTION]
> Należy uważnie używać potwierdzeń, ponieważ mogą one otwierać otwory zabezpieczające i podważać mechanizm środowiska uruchomieniowego w celu wymuszenia ograniczeń zabezpieczeń.  
  
 Potwierdzenia są przydatne w sytuacjach, w których biblioteka wywołuje kod niezarządzany lub wykonuje wywołanie, które wymaga uprawnień, które nie są oczywiście powiązane z zamierzonym użyciem biblioteki. Na przykład, cały kod zarządzany, który wywołuje w kodzie niezarządzanym, musi mieć **SecurityPermission** z określoną flagą **UnmanagedCode** . Kod, który nie pochodzi z komputera lokalnego, na przykład kod pobrany z lokalnego intranetu, nie zostanie domyślnie udzielony. W związku z tym, aby kod pobrany z lokalnego intranetu mógł wywołać bibliotekę, która używa kodu niezarządzanego, musi mieć uprawnienie potwierdzone przez bibliotekę. Ponadto niektóre biblioteki mogą wykonywać wywołania, które nie są widoczne dla obiektów wywołujących i wymagają specjalnych uprawnień.  
  
 Można również użyć potwierdzeń w sytuacjach, w których kod uzyskuje dostęp do zasobu w sposób całkowicie ukryty przez wywołujących. Załóżmy na przykład, że biblioteka uzyskuje informacje z bazy danych, ale w procesie odczytuje również informacje z rejestru komputera. Ponieważ deweloperzy korzystający z biblioteki nie mają dostępu do źródła, nie mogą oni znać, że ich kod wymaga **RegistryPermission** , aby móc korzystać z kodu. W takim przypadku, jeśli zdecydujesz, że nie jest to uzasadnione ani konieczne, aby wymagać, aby wywołujący kod miał uprawnienia dostępu do rejestru, możesz postanowić się, że uprawnienia do odczytu rejestru. W takiej sytuacji odpowiednie jest, aby Biblioteka pomogła uzyskać odpowiednie uprawnienia, aby obiekty wywołujące bez **RegistryPermission** mogły korzystać z biblioteki.  
  
 Potwierdzenie ma wpływ na stos przeszukiwania tylko wtedy, gdy potwierdzone uprawnienie i uprawnienia, które są żądane przez obiekt wywołujący podrzędny, są tego samego typu, a żądanie z uprawnieniami jest podzbiorem potwierdzonego uprawnienia. Na przykład Jeśli postanowisz **FileIOPermission** o odczytaniu wszystkich plików na dysku C i przeniesieniu żądania podrzędnego dla **FileIOPermission** do odczytu plików w katalogu C:\Temp, potwierdzenie może wpłynąć na przechodzenie stosu; Jeśli jednak żądanie dotyczyło **FileIOPermission** zapisu na dysku C, potwierdzenie nie będzie miało żadnego wpływu.  
  
 Aby wykonać potwierdzenia, Twój kod musi mieć przyznane zarówno odpowiednie uprawnienia, jak i <xref:System.Security.Permissions.SecurityPermission> , które reprezentuje prawo do wykonywania potwierdzeń. Mimo że można potwierdzić, że nie przyznano kodu, potwierdzenie byłoby niemożliwe, ponieważ sprawdzenie zabezpieczeń zakończy się niepowodzeniem, aby potwierdzić pomyślne.  
  
 Na poniższej ilustracji pokazano, co się dzieje wprzypadku użycia potwierdzeń. Załóżmy, że następujące instrukcje są prawdziwe o zestawach A, B, C, E i F oraz dwóch uprawnieniach, P1 i P1A:  
  
- P1A reprezentuje prawo do odczytu plików txt na dysku C.  
  
- P1 reprezentuje prawo do odczytu wszystkich plików na dysku C.  
  
- P1A i P1 są typami **FileIOPermission** , a P1A jest podzbiorem P1.  
  
- Zestawom E i F udzielono uprawnienia P1A.  
  
- Zestawowi C udzielono uprawnienia P1.  
  
- Do zestawów A i B nie udzielono uprawnień P1 ani P1A.  
  
- Metoda A jest zawarta w zestawie A, metoda B jest zawarta w zestawie B i tak dalej.  
  
 ![Diagram przedstawiający zestawy metod Assert.](./media/using-the-assert-method/assert-method-assemblies.gif)    
  
 W tym scenariuszu Metoda A wywołuje wywołania B, B wywołuje C, C wywołuje E, i E wywołuje metodę F. Metoda C potwierdza uprawnienie do odczytu plików na dysku C (uprawnienie P1), a metoda E wymaga uprawnień do odczytu plików txt na dysku C (uprawnienia P1A). Gdy w czasie wykonywania zostanie napotkane żądanie w języku F, zostanie wykonane badanie stosu w celu sprawdzenia uprawnień wszystkich wywołujących F, zaczynając od E. E, przyznano uprawnienia P1A, więc stos przeprowadzi badanie uprawnień C, gdzie wykryto potwierdzenie języka C. Ponieważ uprawnienie żądanie (P1A) jest podzbiorem potwierdzonego uprawnienia (P1), przechodzenie przez stos zostanie zatrzymane i sprawdzanie zabezpieczeń zostanie automatycznie zakończone pomyślnie. Nie ma znaczenia, że zestawy A i B nie uzyskały uprawnień P1A. Przez poproszenie P1, metoda C zapewnia, że jej obiekty wywołujące mogą uzyskać dostęp do zasobów chronionych przez P1, nawet jeśli nie udzielono uprawnień dostępu do tego zasobu.  
  
 W przypadku projektowania biblioteki klas i uzyskiwania dostępu do chronionego zasobu należy w większości przypadków zapewnić zapotrzebowanie na zabezpieczenia wymagające, aby wywołujący klasę mieli odpowiednie uprawnienia. Jeśli klasa następnie wykonuje operację, dla której wiadomo, że większość jej obiektów wywołujących nie ma uprawnień, a jeśli wolisz podjąć odpowiedzialność za zezwolenie tym wywołującemu na wywoływanie kodu, możesz postanowić się, wywołując metodę **Assert** na Obiekt uprawnień, który reprezentuje operację wykonywaną przez kod. Użycie metody **Assert** w ten sposób umożliwia wywoływanie, że zwykle nie można to wywołać w kodzie. W związku z tym, jeśli zostanie potwierdzone uprawnienie, należy upewnić się, że odpowiednie sprawdzenia zabezpieczeń zostały wcześniej wykonane, aby zapobiec nieprawidłowemu użyciu składnika.  
  
 Załóżmy na przykład, że Klasa wysoce zaufanej biblioteki ma metodę, która usuwa pliki. Uzyskuje dostęp do pliku, wywołując niezarządzaną funkcję Win32. Obiekt wywołujący wywołuje metodę **usuwania** kodu, przekazując nazwę pliku do usunięcia, C:\test.txt. W ramach metody **delete** kod tworzy <xref:System.Security.Permissions.FileIOPermission> obiekt reprezentujący dostęp do zapisu do C:\test.txt. (Dostęp do zapisu jest wymagany do usunięcia pliku). Kod następnie wywołuje bezwzględne sprawdzenie zabezpieczeń, wywołując metodę **żądania** obiektu **FileIOPermission** . Jeśli jeden z obiektów wywołujących w stosie wywołań nie ma tego uprawnienia, <xref:System.Security.SecurityException> jest zgłaszany. Jeśli żaden wyjątek nie zostanie zgłoszony, wiadomo, że wszyscy wywołujący mają prawo dostępu do C:\Test.txt. Ponieważ sądzisz, że większość obiektów wywołujących nie będzie miała uprawnień dostępu do kodu niezarządzanego, kod następnie tworzy <xref:System.Security.Permissions.SecurityPermission> obiekt, który reprezentuje prawo do wywoływania kodu niezarządzanego i wywołuje metodę **Assert** obiektu. Na koniec wywołuje niezarządzaną funkcję Win32 w celu usunięcia C:\Text.txt i zwraca kontrolę do obiektu wywołującego.  
  
> [!CAUTION]
> Musisz się upewnić, że Twój kod nie używa potwierdzeń w sytuacjach, w których kod może być używany przez inny kod w celu uzyskania dostępu do zasobu chronionego przez żądane uprawnienie. Na przykład w kodzie, który zapisuje do pliku, którego nazwa jest określona przez obiekt wywołujący jako parametr, nie **FileIOPermission** do zapisu w plikach, ponieważ kod może być otwarty do niewłaściwego użycia przez inną firmę.  
  
 W przypadku użycia bezwzględnej składni zabezpieczenia wywoływanie metody **Assert** dla wielu uprawnień w tej samej metodzie powoduje zgłoszenie wyjątku zabezpieczeń. Zamiast tego należy utworzyć obiekt **PermissionSet** , przekazać mu poszczególne uprawnienia, które mają zostać wywołane, a następnie wywołać metodę **Assert** dla obiektu **PermissionSet** . Metodę **Assert** można wywołać więcej niż raz w przypadku użycia deklaratywnej składni zabezpieczenia.  
  
 Poniższy przykład pokazuje deklaratywną składnię zastępowania kontroli zabezpieczeń przy użyciu metody **Assert** . Należy zauważyć, że składnia **FileIOPermissionAttribute** przyjmuje dwie wartości: <xref:System.Security.Permissions.SecurityAction> Wyliczenie i lokalizację pliku lub katalogu, do którego ma zostać udzielone uprawnienie. Wywołanie metody **Assert** powoduje, że wymagania dostępu `C:\Log.txt` do programu powiodło się, nawet jeśli obiekty wywołujące nie są sprawdzane w celu uzyskania uprawnień dostępu do pliku.  
  
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
  
 Poniższe fragmenty kodu przedstawiają nieprawidłową składnię do zastępowania kontroli zabezpieczeń przy użyciu metody **Assert** . W tym przykładzie jest zadeklarowane wystąpienie obiektu **FileIOPermission** . Jego Konstruktor został przesłany jako **FileIOPermissionAccess. AllAccess** , aby można było zdefiniować dozwolony typ dostępu, po którym następuje ciąg opisujący lokalizację pliku. Po zdefiniowaniu obiektu **FileIOPermission** należy wywołać jego metodę **Assert** , aby zastąpić sprawdzanie zabezpieczeń.  
  
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
- [Atrybuty](../../standard/attributes/index.md)
- [Zabezpieczenia dostępu kodu](code-access-security.md)
