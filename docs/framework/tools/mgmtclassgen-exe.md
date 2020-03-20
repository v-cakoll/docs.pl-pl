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
ms.openlocfilehash: 5e39670fbb40acb999a243ac86683219f3c89e4f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180379"
---
# <a name="mgmtclassgenexe-management-strongly-typed-class-generator"></a>Mgmtclassgen.exe (Zarządzanie generatorem silnie typizowanej klasy)
Narzędzie Management Strongly Typed Class Generator umożliwia szybkie generowanie wcześnie powiązanych klas zarządzanych dla określonej klasy Instrumentacji zarządzania Windows (WMI). Wygenerowana klasa upraszcza kod, który trzeba napisać, aby uzyskać dostęp do wystąpienia klasy WMI.  
  
## <a name="syntax"></a>Składnia  
  
```console  
mgmtclassgen
WMIClass [options]
```  
  
|Argument|Opis|  
|--------------|-----------------|  
|*Klasa WMI*|Klasa Instrumentacji zarządzania Windows, dla której jest generowana wcześnie powiązana klasa zarządzana.|  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/l**  *język*|Określa język, w którym ma zostać wygenerowana wcześnie powiązana klasa zarządzana. Jako argument języka można określić **cs** (C#; default), **VB** (Visual Basic), **MC** (C++) lub **JS** (JScript).|  
|**/m**  *maszyna*|Określa komputer, z którym należy nawiązać połączenie (na tym komputerze znajduje się klasa WMI). Wartością domyślną jest komputer lokalny.|  
|**/n**  *ścieżka*|Określa ścieżkę do przestrzeni nazw usługi WMI zawierającej odpowiednią klasę WMI. Jeśli ta opcja nie zostanie określona, narzędzie wygeneruje kod dla *klasy WMIClass* w domyślnym obszarze nazw **Root\cimv2.**|  
|**/o**  *classnamespace*|Określa przestrzeń nazw platformy .NET, w której ma zostać wygenerowana klasa kodu zarządzanego. Jeśli ta opcja nie zostanie określona, narzędzie wygeneruje przestrzeń nazw, używając przestrzeni nazw usługi WMI i prefiksu schematu. Prefiks schematu jest częścią nazwy klasy poprzedzającą znak podkreślenia. Na przykład dla **klasy Win32_OperatingSystem** w obszarze nazw **Root\cimv2** narzędzie wygeneruje klasę w **katalogu GŁÓWNYM. CIMV2. Win32**.|  
|**/p**  *ścieżka pliku*|Określa ścieżkę do pliku, w którym ma zostać zapisany wygenerowany kod. Jeśli ta opcja nie zostanie określona, narzędzie utworzy plik w bieżącym katalogu. Nazywa klasę i plik, w którym generuje klasę przy użyciu *WMIClass* argument. Nazwa klasy i pliku są takie same jak nazwa *WMIClass.* Jeśli *WMIClass* zawiera znak podkreślenia, narzędzie używa części nazwy klasy po znaku podkreślenia. Na przykład jeśli nazwa *WMIClass* jest w formacie **Win32_LogicalDisk,** wygenerowana klasa i plik nosi nazwę "logicaldisk". Jeżeli plik już istnieje, narzędzie zastąpi istniejący plik.|  
|**/pw**  *hasło*|Określa hasło, które ma być używane podczas logowania się do komputera określonego przez opcję **/m.**|  
|**/u**  *nazwa użytkownika*|Określa nazwę użytkownika, która ma być używana podczas logowania do komputera określonego przez opcję **/m.**|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 Program Mgmtclassgen.exe <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> używa metody. Dzięki temu można użyć dowolnego niestandardowego dostawcy kodu, aby wygenerować kod w zarządzanych językach innych niż C#, Visual Basic i JScript.  
  
 Należy zauważyć, że wygenerowane klasy są powiązane ze schematem, dla którego są generowane. Jeśli schemat źródłowy ulegnie zmianie, trzeba ponownie wygenerować klasę, jeśli chce się odzwierciedlić zmiany w schemacie.  
  
 W poniższej tabeli pokazano mapowanie typów modelu wspólnych informacji (CIM) usługi WMI na typy danych w generowanej klasie:  
  
|Typ modelu CIM|Typ danych w generowanej klasie|  
|--------------|--------------------------------------|  
|CIM_SINT8|**Sbyte**|  
|CIM_UINT8|**Byte**|  
|CIM_SINT16|**Int16**|  
|CIM_UINT16|**UInt16**|  
|CIM_SINT32|**Int32**|  
|SIM_UINT32|**UInt32**|  
|CIM_SINT64|**Int64 ( int64 )**|  
|CIM_UINT64|**UInt64**|  
|CIM_REAL32|**Single**|  
|CIM_REAL64|**Podwójne**|  
|CIM_BOOLEAN|**Wartość logiczna**|  
|CIM_String|**Ciąg**|  
|CIM_DATETIME|**DateTime** lub **TimeSpan**|  
|CIM_REFERENCE|**Managementpath**|  
|CIM_CHAR16|**Char**|  
|CIM_OBJECT|**Managementbaseobject**|  
|CIM_IUNKNOWN|**Obiektu**|  
|CIM_ARRAY|Tablica wymienionych powyżej obiektów|  
  
 Podczas generowania klasy WMI należy zwrócić uwagę na następujące zachowania:  
  
- Możliwe jest, że standardowa publiczna właściwość lub metoda będzie miała taką samą nazwę jak istniejąca właściwość lub metoda. Jeśli tak się zdarzy, narzędzie zmieni nazwę właściwości lub metody w generowanej klasie w celu uniknięcia konfliktu nazw.  
  
- Możliwe jest, że nazwa właściwości lub metody w generowanej klasie będzie słowem kluczowym w docelowym języku programowania. Jeśli tak się zdarzy, narzędzie zmieni nazwę właściwości lub metody w generowanej klasie w celu uniknięcia konfliktu nazw.  
  
- W usłudze WMI kwalifikatory to modyfikatory zawierające informacje opisujące klasę, wystąpienie, właściwość lub metodę. Usługa WMI używa standardowych kwalifikatorów, takich jak **Odczyt,** **Zapis**i **Klucz,** do opisania właściwości w wygenerowanej klasie. Na przykład właściwość, która jest modyfikowana za pomocą **Read** kwalifikator jest zdefiniowany tylko z właściwości **get** akcesor w klasie generowane. Ponieważ właściwość oznaczona kwalifikatorem **Odczytu** jest przeznaczona tylko do odczytu, **zestaw** akcesor nie jest zdefiniowany.  
  
- Właściwość liczbowa może być modyfikowana przez **wartości** i **ValueMaps** kwalifikatorów, aby wskazać, że właściwość można ustawić tylko do określonych wartości dopuszczalnych. Wyliczenie jest generowane z tych **wartości** i **ValueMaps** i właściwość jest mapowana do wyliczenia.  
  
- Usługa WMI używa pojedynczego terminu w celu opisania klasy, która ma tylko jedno wystąpienie. W związku z tym konstruktora bez parametrów dla klasy singleton zaikwuje klasy do jedynego wystąpienia klasy.  
  
- Klasa WMI może mieć właściwości, które są obiektami. Podczas generowania silnie typizowanej klasy dla klasy WMI tego typu należy wziąć pod uwagę wygenerowanie silnie typizowanych klas dla typów właściwości osadzonych obiektów. Umożliwi to dostęp do osadzonych obiektów w silnie typizowany sposób. Należy zauważyć, że wygenerowany kod może nie być w stanie wykryć typu osadzonego obiektu. W takim przypadku w wygenerowanym kodzie zostanie utworzony komentarz powiadamiający o problemie. Następnie można zmodyfikować wygenerowany kod, tak aby właściwość miała typ innej generowanej klasy.  
  
- W usłudze WMI wartość danych typu CIM_DATETIME może przedstawiać określoną datę i godzinę albo interwał czasu. Jeśli wartość danych reprezentuje datę i godzinę, typem danych w wygenerowanej klasie jest **DateTime**. Jeśli wartość danych reprezentuje przedział czasu, typem danych w wygenerowanej klasie jest **TimeSpan**.  
  
 Alternatywnie można wygenerować silnie typizowaną klasę, używając rozszerzenia zarządzania Eksploratora serwera w programie Visual Studio .NET.  
  
 Aby uzyskać więcej informacji na temat usługi WMI, zobacz temat **Instrumentacji zarządzania windowsiem** w dokumentacji zestawu SDK platformy.  
  
## <a name="examples"></a>Przykłady  
 Następujące polecenie generuje klasę zarządzaną w kodzie języka C# dla **Win32_LogicalDisk** klasy WMI w obszarze nazw **Root\cimv2.** Narzędzie zapisuje klasę zarządzana do pliku źródłowego w c:\disk.cs w **katalogu głównym. CIMV2. Obszar nazw win32.**  
  
```console  
mgmtclassgen Win32_LogicalDisk /n root\cimv2 /l CS /p c:\disk.cs  
```  
  
 W poniższym przykładzie kodu pokazano, w jaki sposób można programowo używać wygenerowanej klasy. Najpierw jest wyliczane wystąpienie klasy i jest drukowana ścieżka. Następnie za pomocą wystąpienia usługi WMI jest tworzone wystąpienie wygenerowanej klasy, które ma zostać zainicjowane. `Process`jest klasą **Win32_Process** generowaną dla `LogicalDisk` Win32_Process i jest klasą generowaną dla **Win32_LogicalDisk** w obszarze nazw **Root\cimv2.**  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Management>
- <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType>
- <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>
- [narzędzia](index.md)
- [Wiersz polecenia](developer-command-prompt-for-vs.md)
