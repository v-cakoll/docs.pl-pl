---
title: Mgmtclassgen.exe (Zarządzanie generatorem silnie typizowanej klasy)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CIM types
- Management Strongly Typed Class Generator
- WMI class
- Mgmtclassgen.exe
- early-bound managed classes
ms.assetid: 02ce6699-49b5-4a0b-b0d5-1003c491232e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60f48422d23fc5db743eeb05e3eddeb732bff102
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364023"
---
# <a name="mgmtclassgenexe-management-strongly-typed-class-generator"></a>Mgmtclassgen.exe (Zarządzanie generatorem silnie typizowanej klasy)
Narzędzie Management Strongly Typed Class Generator umożliwia szybkie generowanie wcześnie powiązanych klas zarządzanych dla określonej klasy Instrumentacji zarządzania Windows (WMI). Wygenerowana klasa upraszcza kod, który trzeba napisać, aby uzyskać dostęp do wystąpienia klasy WMI.  
  
## <a name="syntax"></a>Składnia  
  
```  
mgmtclassgen   
WMIClass [options]   
```  
  
|Argument|Opis|  
|--------------|-----------------|  
|*WMIClass*|Klasa Instrumentacji zarządzania Windows, dla której jest generowana wcześnie powiązana klasa zarządzana.|  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/l** *języka*|Określa język, w którym ma zostać wygenerowana wcześnie powiązana klasa zarządzana. Jako argumentu języka  można określićC#cs (; default), **VB** (Visual Basic),C++ **MC** () lub **js** (JScript).|  
|**/m** *maszyny*|Określa komputer, z którym należy nawiązać połączenie (na tym komputerze znajduje się klasa WMI). Wartością domyślną jest komputer lokalny.|  
|**/n** *ścieżki*|Określa ścieżkę do przestrzeni nazw usługi WMI zawierającej odpowiednią klasę WMI. Jeśli ta opcja nie zostanie określona, narzędzie generuje kod dla *WMIClass* w domyślnej przestrzeni nazw **root\cimv2** .|  
|**/o** *classnamespace*|Określa przestrzeń nazw platformy .NET, w której ma zostać wygenerowana klasa kodu zarządzanego. Jeśli ta opcja nie zostanie określona, narzędzie wygeneruje przestrzeń nazw, używając przestrzeni nazw usługi WMI i prefiksu schematu. Prefiks schematu jest częścią nazwy klasy poprzedzającą znak podkreślenia. Na przykład dla klasy **Win32_OperatingSystem** w przestrzeni nazw **root\cimv2** narzędzie wygeneruje klasę w **katalogu głównym. CIMV2. Win32**.|  
|**/p** *filepath*|Określa ścieżkę do pliku, w którym ma zostać zapisany wygenerowany kod. Jeśli ta opcja nie zostanie określona, narzędzie utworzy plik w bieżącym katalogu. Nazwa klasy i pliku, w którym generuje klasę przy użyciu argumentu *WMIClass* . Nazwa klasy i pliku jest taka sama jak nazwa *WMIClass.* Jeśli *WMIClass* zawiera znak podkreślenia, narzędzie używa części nazwy klasy po znaku podkreślenia. Na przykład jeśli nazwa *WMIClass* ma format **Win32_LogicalDisk**, wygenerowana Klasa i plik o nazwie "dysk logiczny". Jeżeli plik już istnieje, narzędzie zastąpi istniejący plik.|  
|**/PW** *hasła*|Określa hasło, które ma być używane podczas logowania do komputera określonego przez **/m** Option.|  
|**/u** *nazwy użytkownika*|Określa nazwę użytkownika, która ma być używana podczas logowania do komputera określonego przez **/m** Option.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 Mgmtclassgen. exe używa <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> metody. Dzięki temu można użyć dowolnego niestandardowego dostawcy kodu, aby wygenerować kod w zarządzanych językach innych niż C#, Visual Basic i JScript.  
  
 Należy zauważyć, że wygenerowane klasy są powiązane ze schematem, dla którego są generowane. Jeśli schemat źródłowy ulegnie zmianie, trzeba ponownie wygenerować klasę, jeśli chce się odzwierciedlić zmiany w schemacie.  
  
 W poniższej tabeli pokazano mapowanie typów modelu wspólnych informacji (CIM) usługi WMI na typy danych w generowanej klasie:  
  
|Typ modelu CIM|Typ danych w generowanej klasie|  
|--------------|--------------------------------------|  
|CIM_SINT8|**SByte**|  
|CIM_UINT8|**Byte**|  
|CIM_SINT16|**Int16**|  
|CIM_UINT16|**UInt16**|  
|CIM_SINT32|**Int32**|  
|SIM_UINT32|**Równ**|  
|CIM_SINT64|**Int64**|  
|CIM_UINT64|**UInt64**|  
|CIM_REAL32|**Single**|  
|CIM_REAL64|**Double**|  
|CIM_BOOLEAN|**Boolean**|  
|CIM_String|**Ciąg**|  
|CIM_DATETIME|**DateTime** lub **TimeSpan**|  
|CIM_REFERENCE|**ManagementPath**|  
|CIM_CHAR16|**Delikatn**|  
|CIM_OBJECT|**ManagementBaseObject**|  
|CIM_IUNKNOWN|**Obiekt**|  
|CIM_ARRAY|Tablica wymienionych powyżej obiektów|  
  
 Podczas generowania klasy WMI należy zwrócić uwagę na następujące zachowania:  
  
- Możliwe jest, że standardowa publiczna właściwość lub metoda będzie miała taką samą nazwę jak istniejąca właściwość lub metoda. Jeśli tak się zdarzy, narzędzie zmieni nazwę właściwości lub metody w generowanej klasie w celu uniknięcia konfliktu nazw.  
  
- Możliwe jest, że nazwa właściwości lub metody w generowanej klasie będzie słowem kluczowym w docelowym języku programowania. Jeśli tak się zdarzy, narzędzie zmieni nazwę właściwości lub metody w generowanej klasie w celu uniknięcia konfliktu nazw.  
  
- W usłudze WMI kwalifikatory to modyfikatory zawierające informacje opisujące klasę, wystąpienie, właściwość lub metodę. Usługa WMI używa kwalifikatorów standardowych, takich jak **Odczyt**, **zapis**i **klucz** , aby opisać właściwość w wygenerowanej klasie. Na przykład właściwość, która jest modyfikowana przy użyciu kwalifikatora **odczytu** , jest definiowana tylko przy użyciu metody dostępu **Get** właściwości w wygenerowanej klasie. Ponieważ właściwość oznaczona kwalifikatorem **odczytu** jest przeznaczona tylko do odczytu, metoda dostępu **Set** nie jest zdefiniowana.  
  
- Właściwość numeryczna może być modyfikowana przez kwalifikatory **wartości** i **ValueMaps** , aby wskazać, że właściwość można ustawić tylko dla określonych dozwolonych wartości. Wyliczenie jest generowane z tymi **wartościami** i **ValueMaps** , a właściwość jest zamapowana na Wyliczenie.  
  
- Usługa WMI używa pojedynczego terminu w celu opisania klasy, która ma tylko jedno wystąpienie. W związku z tym, Konstruktor bez parametrów dla klasy pojedynczej będzie inicjować klasę tylko do wystąpienia klasy.  
  
- Klasa WMI może mieć właściwości, które są obiektami. Podczas generowania silnie typizowanej klasy dla klasy WMI tego typu należy wziąć pod uwagę wygenerowanie silnie typizowanych klas dla typów właściwości osadzonych obiektów. Umożliwi to dostęp do osadzonych obiektów w silnie typizowany sposób. Należy zauważyć, że wygenerowany kod może nie być w stanie wykryć typu osadzonego obiektu. W takim przypadku w wygenerowanym kodzie zostanie utworzony komentarz powiadamiający o problemie. Następnie można zmodyfikować wygenerowany kod, tak aby właściwość miała typ innej generowanej klasy.  
  
- W usłudze WMI wartość danych typu CIM_DATETIME może przedstawiać określoną datę i godzinę albo interwał czasu. Jeśli wartość danych reprezentuje datę i godzinę, typem danych w generowanej klasie jest **DateTime**. Jeśli wartość danych reprezentuje przedział czasu, typem danych w generowanej klasie jest **TimeSpan**.  
  
 Alternatywnie można wygenerować silnie typizowaną klasę, używając rozszerzenia zarządzania Eksploratora serwera w programie Visual Studio .NET.  
  
 Aby uzyskać więcej informacji na temat usługi WMI, zobacz temat **Instrumentacja zarządzania Windows** w dokumentacji zestawu SDK platformy.  
  
## <a name="examples"></a>Przykłady  
 Następujące polecenie generuje klasę zarządzaną w C# kodzie dla klasy WMI usługi **Win32_LogicalDisk** w przestrzeni nazw **root\cimv2** . Narzędzie zapisuje klasę zarządzaną w pliku źródłowym w c:\disk.cs w **katalogu głównym. CIMV2.** Przestrzeń nazw Win32.  
  
```  
mgmtclassgen Win32_LogicalDisk /n root\cimv2 /l CS /p c:\disk.cs  
```  
  
 W poniższym przykładzie kodu pokazano, w jaki sposób można programowo używać wygenerowanej klasy. Najpierw jest wyliczane wystąpienie klasy i jest drukowana ścieżka. Następnie za pomocą wystąpienia usługi WMI jest tworzone wystąpienie wygenerowanej klasy, które ma zostać zainicjowane. `Process`jest klasą wygenerowaną  dla Win32_Process `LogicalDisk` i jest klasą wygenerowaną dla klasy **Win32_LogicalDisk** w przestrzeni nazw **root\cimv2** .  
  
```vb  
Imports System  
Imports System.Management  
Imports ROOT.CIMV2.Win32  
  
Public Class App     
   Public Shared Sub Main()        
      ' Enumerate instances of the Win32_process.  
      ' Print the Name property of the instance.  
      Dim ps As Process     
      For Each ps In  Process.GetInstances()  
         Console.WriteLine(ps.Name)  
      Next ps  
  
      ' Initialize the instance of LogicalDisk with  
      ' the WMI instance pointing to logical drive d:.  
      Dim dskD As New LogicalDisk(New _  
         ManagementPath("win32_LogicalDisk.DeviceId=""d:"""))  
      Console.WriteLine(dskD.Caption)  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Management;  
using ROOT.CIMV2.Win32;  
  
public class App  
{  
   public static void Main()  
   {  
      // Enumerate instances of the Win32_process.  
      // Print the Name property of the instance.  
      foreach(Process ps in Process.GetInstances())  
      {  
         Console.WriteLine(ps.Name);  
      }  
  
      // Initialize the instance of LogicalDisk with  
      // the WMI instance pointing to logical drive d:.  
      LogicalDisk dskD = new LogicalDisk(new ManagementPath(  
        "win32_LogicalDisk.DeviceId=\"d:\""));  
      Console.WriteLine(dskD.Caption);  
   }  
}  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Management>
- <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType>
- <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>
- [Narzędzia](../../../docs/framework/tools/index.md)
- [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
