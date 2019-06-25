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
ms.openlocfilehash: 9e018d8c83165b3e025ad4db7f3d59b6ba58b72a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64616094"
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
|**/l** *języka*|Określa język, w którym ma zostać wygenerowana wcześnie powiązana klasa zarządzana. Można określić **CS** (C#; domyślna), **VB** (Visual Basic), **MC** (C++) lub **JS** (JScript) jako argument języka.|  
|**/m** *maszyny*|Określa komputer, z którym należy nawiązać połączenie (na tym komputerze znajduje się klasa WMI). Wartością domyślną jest komputer lokalny.|  
|**/n** *ścieżki*|Określa ścieżkę do przestrzeni nazw usługi WMI zawierającej odpowiednią klasę WMI. Jeśli ta opcja nie jest określona, narzędzie wygeneruje kod dla *WMIClass* w domyślnym **Root\cimv2** przestrzeni nazw.|  
|**/o** *classnamespace*|Określa przestrzeń nazw platformy .NET, w której ma zostać wygenerowana klasa kodu zarządzanego. Jeśli ta opcja nie zostanie określona, narzędzie wygeneruje przestrzeń nazw, używając przestrzeni nazw usługi WMI i prefiksu schematu. Prefiks schematu jest częścią nazwy klasy poprzedzającą znak podkreślenia. Na przykład w przypadku **Win32_OperatingSystem** klasy w **Root\cimv2** przestrzeni nazw, narzędzie wygeneruje klasy w **głównego. CIMV2. Win32**.|  
|**/p** *filepath*|Określa ścieżkę do pliku, w którym ma zostać zapisany wygenerowany kod. Jeśli ta opcja nie zostanie określona, narzędzie utworzy plik w bieżącym katalogu. Nazwa klasy oraz pliku, w którym jest generowana, przy użyciu klasy *WMIClass* argumentu. Nazwa klasy i pliku są takie same jak nazwa *WMIClass.* Jeśli *WMIClass* zawiera znak podkreślenia, narzędzie użyje części nazwy klasy po znaku podkreślenia. Na przykład jeśli *WMIClass* nazwa jest w formacie **Win32_LogicalDisk**, wygenerowana klasa oraz plik nosi nazwę "DyskLogiczny". Jeżeli plik już istnieje, narzędzie zastąpi istniejący plik.|  
|**/PW** *hasła*|Określa hasło używane podczas logowania do komputera określonego przez **/m** opcji.|  
|**/u** *nazwy użytkownika*|Określa nazwę użytkownika do użycia podczas logowania się do komputera określonego przez **/m** opcji.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 MgmtClassGen.exe używa <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> metody. Dzięki temu można użyć dowolnego niestandardowego dostawcy kodu, aby wygenerować kod w zarządzanych językach innych niż C#, Visual Basic i JScript.  
  
 Należy zauważyć, że wygenerowane klasy są powiązane ze schematem, dla którego są generowane. Jeśli schemat źródłowy ulegnie zmianie, trzeba ponownie wygenerować klasę, jeśli chce się odzwierciedlić zmiany w schemacie.  
  
 W poniższej tabeli pokazano mapowanie typów modelu wspólnych informacji (CIM) usługi WMI na typy danych w generowanej klasie:  
  
|Typ modelu CIM|Typ danych w generowanej klasie|  
|--------------|--------------------------------------|  
|CIM_SINT8|**SByte**|  
|CIM_UINT8|**Byte**|  
|CIM_SINT16|**Int16**|  
|CIM_UINT16|**UInt16**|  
|CIM_SINT32|**Int32**|  
|SIM_UINT32|**UInt32**|  
|CIM_SINT64|**Int64**|  
|CIM_UINT64|**UInt64 —**|  
|CIM_REAL32|**Single**|  
|CIM_REAL64|**Double**|  
|CIM_BOOLEAN|**Boolean**|  
|CIM_String|**Ciąg**|  
|CIM_DATETIME|**Data i godzina** lub **przedział czasu**|  
|CIM_REFERENCE|**ManagementPath**|  
|CIM_CHAR16|**Char**|  
|CIM_OBJECT|**ManagementBaseObject**|  
|CIM_IUNKNOWN|**Obiekt**|  
|CIM_ARRAY|Tablica wymienionych powyżej obiektów|  
  
 Podczas generowania klasy WMI należy zwrócić uwagę na następujące zachowania:  
  
- Możliwe jest, że standardowa publiczna właściwość lub metoda będzie miała taką samą nazwę jak istniejąca właściwość lub metoda. Jeśli tak się zdarzy, narzędzie zmieni nazwę właściwości lub metody w generowanej klasie w celu uniknięcia konfliktu nazw.  
  
- Możliwe jest, że nazwa właściwości lub metody w generowanej klasie będzie słowem kluczowym w docelowym języku programowania. Jeśli tak się zdarzy, narzędzie zmieni nazwę właściwości lub metody w generowanej klasie w celu uniknięcia konfliktu nazw.  
  
- W usłudze WMI kwalifikatory to modyfikatory zawierające informacje opisujące klasę, wystąpienie, właściwość lub metodę. Usługa WMI używa standardowych kwalifikatorów, takich jak **odczytu**, **zapisu**, i **klucz** do opisywania właściwości w generowanej klasie. Na przykład właściwość modyfikowana przez **odczytu** kwalifikator jest zdefiniowana tylko z właściwością **uzyskać** metody dostępu w generowanej klasie. Właściwość jest oznaczona za pomocą **odczytu** kwalifikator jest przeznaczony tylko do odczytu do **ustaw** dostępu nie jest zdefiniowany.  
  
- Właściwość liczbowa może być modyfikowana przez **wartości** i **ValueMaps** kwalifikatorów, aby wskazać, że właściwość można ustawić tylko do określone dozwolone wartości. Jest generowane wyliczenie **wartości** i **ValueMaps** i właściwość jest mapowana do wyliczenia.  
  
- Usługa WMI używa pojedynczego terminu w celu opisania klasy, która ma tylko jedno wystąpienie. Dlatego też konstruktor domyślny klasy pojedynczej będzie inicjował klasę wyłącznie do jednego wystąpienia.  
  
- Klasa WMI może mieć właściwości, które są obiektami. Podczas generowania silnie typizowanej klasy dla klasy WMI tego typu należy wziąć pod uwagę wygenerowanie silnie typizowanych klas dla typów właściwości osadzonych obiektów. Umożliwi to dostęp do osadzonych obiektów w silnie typizowany sposób. Należy zauważyć, że wygenerowany kod może nie być w stanie wykryć typu osadzonego obiektu. W takim przypadku w wygenerowanym kodzie zostanie utworzony komentarz powiadamiający o problemie. Następnie można zmodyfikować wygenerowany kod, tak aby właściwość miała typ innej generowanej klasy.  
  
- W usłudze WMI wartość danych typu CIM_DATETIME może przedstawiać określoną datę i godzinę albo interwał czasu. Jeśli wartość danych przedstawia datę i godzinę, typem danych w generowanej klasie jest **daty/godziny**. Jeśli wartość danych przedstawia interwał czasu, typem danych w generowanej klasie jest **TimeSpan**.  
  
 Alternatywnie można wygenerować silnie typizowaną klasę, używając rozszerzenia zarządzania Eksploratora serwera w programie Visual Studio .NET.  
  
 Aby uzyskać więcej informacji na temat usługi WMI, zobacz **Instrumentacji zarządzania Windows** temat w dokumentacji zestawu SDK platformy.  
  
## <a name="examples"></a>Przykłady  
 Następujące polecenie generuje zarządzaną klasę w C# kod **Win32_LogicalDisk** klasy usługi WMI w **Root\cimv2** przestrzeni nazw. Narzędzie zapisuje plik źródłowy w c:\disk.cs w klasy zarządzanej **głównego. CIMV2. Win32** przestrzeni nazw.  
  
```  
mgmtclassgen Win32_LogicalDisk /n root\cimv2 /l CS /p c:\disk.cs  
```  
  
 W poniższym przykładzie kodu pokazano, w jaki sposób można programowo używać wygenerowanej klasy. Najpierw jest wyliczane wystąpienie klasy i jest drukowana ścieżka. Następnie za pomocą wystąpienia usługi WMI jest tworzone wystąpienie wygenerowanej klasy, które ma zostać zainicjowane. `Process` jest to klasa generowana dla **Win32_Process** i `LogicalDisk` to klasa generowana dla **Win32_LogicalDisk** w **Root\cimv2** przestrzeni nazw.  
  
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
