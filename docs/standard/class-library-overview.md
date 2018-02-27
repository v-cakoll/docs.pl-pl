---
title: "Przegląd biblioteki klas programu .NET"
ms.custom: 
ms.date: 02/08/2018
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- classes [.NET Framework], library overview
- classes [.NET Core], library overview
- .NET, library overview
- class objects value type
- naming conventions [.NET Framework]
- types, .NET Framework
- user-defined types
- Visual Basic, data types
- data types [.NET Framework], C++
- Visual C#, data types
- libraries, .NET Framework class library
- data types [.NET Framework], F#
- System namespace
- F#, data types
- .NET Framework, class library
- type system [.NET Framework]
- data types [.NET Framework]
- value types
- data types [.NET Framework], Visual Basic
- Common Language Specification
- namespaces [.NET Framework]
- floating point value type
- class library [.NET Framework]
- CLS
- logical value type
- .NET Framework class library, about
- built-in types
- namespaces [.NET Framework], about namespaces
- Visual C++, data types
- members [.NET Framework], type
- data types [.NET Framework], C#
- integer value type
- base types, class library
ms.assetid: 7e4c5921-955d-4b06-8709-101873acf157
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ffa64d3a1f9ade7a97b15edfdecbad566c871c12
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="net-class-library-overview"></a>Przegląd biblioteki klas programu .NET
Implementacje .NET zawierają klasy, interfejsy delegatów i typy wartości, które przyspieszenia i zoptymalizować proces rozwoju i zapewnienia dostępu do funkcji systemu. W celu ułatwienia współdziałanie między językami, większość typów .NET są zgodne ze specyfikacją CLS i w związku z tym można używać z dowolnego języka programowania, w których kompilatora odpowiada specyfikacja języka wspólnego (ze specyfikacją CLS).  
  
 Typy .NET są foundation na .NET, które są wbudowane aplikacji, składników i kontrolek. Implementacje .NET obejmują typy, które wykonują następujące funkcje:  
  
-   Reprezentuje podstawowe typy danych i wyjątki.  
  
-   Hermetyzuj struktury danych.  
  
-   Wykonywanie operacji We/Wy.  
  
-   Dostęp do informacji o typach załadowany.  
  
-   Wywołania sprawdzania zabezpieczeń .NET Framework.  
  
-   Zapewnianie dostępu do danych, sformatowanego graficznego interfejsu użytkownika po stronie klienta i kontrolowane przez serwer, po stronie klienta graficznego interfejsu użytkownika.  
  
 .NET zawiera bogaty zestaw interfejsów, a także abstrakcyjna i konkretnych klas (system inny niż ogólny). Można używać konkretnych klas bez zmian lub w wielu przypadkach, pochodzi z ich własnych klas. Aby korzystać z funkcji interfejsu, należy utworzyć klasę, która implementuje interfejs lub wyprowadzenia klasy z jednej z klas .NET Framework, które implementuje interfejs.  
  
## <a name="naming-conventions"></a>Konwencje nazewnictwa  
 Typy .NET Użyj schemat nazewnictwa kropka składni, które connotes hierarchii. Ta technika grupuje powiązanych typów w przestrzeni nazw, mogą być przeszukiwane i łatwiej odwołania. Pierwsza część pełną nazwę — maksymalnie kropki (.) po prawej stronie — jest nazwą przestrzeni nazw. Ostatnia część nazwa jest nazwą typu. Na przykład **System.Collections.ArrayList** reprezentuje **ArrayList** typu, który należy do **System.Collections** przestrzeni nazw. Typy w **System.Collections** może służyć do modyfikowania kolekcji obiektów.  
  
 Ten schemat nazewnictwa ułatwia deweloperom biblioteki rozszerzanie [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] do tworzenia grup hierarchicznych typów i nazw je w sposób spójny, informacyjny. Umożliwia także typy jednoznacznie zidentyfikować przez ich pełną nazwę (oznacza to, według nazwy przestrzeni nazw i typ), co uniemożliwia konflikty nazw typu. Deweloperzy biblioteki oczekuje się podczas tworzenia nazw dla ich nazw, użyj następującej konwencji:  
  
 *CompanyName*.*TechnologyName*  
  
 Na przykład przestrzeni nazw Microsoft.Word odpowiada Niniejsze wytyczne.  
  
 Użyj wzorców nazewnictwa do grupy powiązanych typów w przestrzeni nazw jest bardzo przydatny sposób tworzenia i zarządzania dokumentami biblioteki klas. Jednak ten schemat nazewnictwa nie ma wpływu na widoczność, dostęp do elementu członkowskiego, dziedziczenia, zabezpieczeń lub powiązanie. Przestrzeń nazw może być podzielonym na partycje w wielu zestawów i jednym zestawie może zawierać typów z kilku obszarów nazw. Zestaw zawiera formalnej struktury przechowywania wersji, wdrażania, zabezpieczeń, ładowanie i wgląd w środowisko uruchomieniowe języka wspólnego.  
  
 Aby uzyskać więcej informacji o nazwach obszarów nazw i typ, zobacz [Wspólny System typów](../../docs/standard/base-types/common-type-system.md).  
  
## <a name="system-namespace"></a>Namespace systemu  
 <xref:System> Przestrzeń nazw jest przestrzeń nazw korzenia dla podstawowych typów programu .NET. Ta przestrzeń nazw zawiera klasy reprezentujące podstawowe typy danych używany przez wszystkie aplikacje: <xref:System.Object> (głównym hierarchii dziedziczenia), <xref:System.Byte>, <xref:System.Char>, <xref:System.Array>, <xref:System.Int32>, <xref:System.String>i tak dalej. Wiele z tych typów odpowiadają typy pierwotne danych, które używa języka programowania. Podczas pisania kodu przy użyciu typów .NET Framework, można użyć danego języka odpowiednie słowo kluczowe podczas .NET Framework jest oczekiwany typ danych podstawowych.  
  
 Poniższa tabela zawiera listę typów podstawowych, że .NET dostarcza krótko opisano każdy typ i wskazuje danego typu w Visual Basic, C#, C++ i F #.  
  
|Kategoria|Nazwa klasy|Opis|Typ danych Visual Basic|C# — typ danych|C + +/ CLI — typ danych|Typ danych F #|  
|--------------|----------------|-----------------|----------------------------|-------------------|---------------------|-----------------------|  
|Liczba całkowita|<xref:System.Byte>|8-bitową nieznakowaną liczbą całkowitą.|**Byte**|**byte**|**char bez znaku**|**byte**|  
||<xref:System.SByte>|8-bitową liczbę całkowitą ze znakiem.<br /><br /> Nie zgodne z CLS.|**SByte**|**sbyte**|**char**<br /> —lub—<br /> **podpisana** **char**|**sbyte**|  
||<xref:System.Int16>|16-bitową liczbę całkowitą ze znakiem.|**Short**|**short**|**short**|**int16**|  
||<xref:System.Int32>|Całkowita 32-bitowych.|**Integer**|**int**|**int**<br /><br /> —lub—<br /><br /> **long**|**int**|  
||<xref:System.Int64>|Całkowita 64-bitowych.|**długa**|**long**|**__int64**|**int64**|  
||<xref:System.UInt16>|16-bitową liczbę całkowitą bez znaku.<br /><br /> Nie zgodne z CLS.|**UShort**|**ushort**|**short bez znaku**|**uint16**|  
||<xref:System.UInt32>|32-bitowa liczba całkowita bez znaku.<br /><br /> Nie zgodne z CLS.|**Uinteger —**|**uint**|**unsigned int**<br /> —lub—<br /> **unsigned long**|**uint32**|  
||<xref:System.UInt64>|64-bitowa liczba całkowita bez znaku.<br /><br /> Nie zgodne z CLS.|**ULong**|**ulong**|**__int64 bez znaku**|**uint64**|  
|Liczba zmiennoprzecinkowa|<xref:System.Single>|Liczby zmiennoprzecinkowe (32-bitowy) pojedynczej precyzji.|**Pojedynczy**|**float**|**float**|**float32**</br> lub</br>**single**|  
||<xref:System.Double>|Liczba zmiennoprzecinkowa (64-bitowy) podwójnej precyzji.|**O podwójnej precyzji**|**double**|**double**|**float**</br> lub </br> **double**|  
|Logiczne|<xref:System.Boolean>|Wartość logiczna (true lub false).|**Boolean**|**bool**|**bool**|**bool**|  
|Inne|<xref:System.Char>|Znak Unicode (16-bitowe).|**char**|**char**|**wchar_t**|**char**|  
||<xref:System.Decimal>|Wartość dziesiętna (128-bitowe).|**Decimal**|**decimal**|**Decimal**|**decimal**|  
||<xref:System.IntPtr>|Całkowita którego rozmiar jest zależna od podstawowej platformy (32-bitową wartość na platformie 32-bitowy) oraz wartość 64-bitowym na 64-bitowej platformy.|**IntPtr**<br /><br /> Brak typu wbudowanego.|**IntPtr**<br /><br /> Brak typu wbudowanego.|**IntPtr**<br /><br /> Brak typu wbudowanego.|**unativeint**|  
||<xref:System.UIntPtr>|Całkowitą bez znaku, którego rozmiar jest zależna od podstawowej platformy (32-bitową wartość na platformie 32-bitowy) oraz wartość 64-bitowym na 64-bitowej platformy.<br /><br /> Nie zgodne z CLS.|**UIntPtr**<br /><br /> Brak typu wbudowanego.|**UIntPtr**<br /><br /> Brak typu wbudowanego.|**UIntPtr**<br /><br /> Brak typu wbudowanego.|**unativeint**|  
||<xref:System.Object>|Element główny hierarchii obiektów.|**Object**|**object**|**Object^**|**obj**|  
||<xref:System.String>|Niezmienne, o stałej długości ciągu znaków Unicode.|**Ciąg**|**string**|**String ^**|**string**|  
  
 Oprócz podstawowe typy danych <xref:System> przestrzeń nazw zawiera klasy ponad 100, począwszy od klasy, które obsługi wyjątków do klasy, które zajmują się podstawowe koncepcje środowiska uruchomieniowego, takich jak moduł garbage collector i domen aplikacji. <xref:System> Przestrzeń nazw zawiera także wiele nazw drugiego poziomu.  
  
 Aby uzyskać więcej informacji na temat obszarów nazw, należy użyć [przeglądarki interfejs API .NET](https://docs.microsoft.com/dotnet/api) do przeglądania w bibliotece klas programu .NET. Dokumentacji interfejsu API zawiera dokumentacja dla każdej przestrzeni nazw, jego typów i wszystkich ich elementy członkowskie.  
  
## <a name="see-also"></a>Zobacz też  
 [System typu wspólnego](../../docs/standard/base-types/common-type-system.md)  
 [Przeglądarka interfejs API .NET](https://docs.microsoft.com/dotnet/api)  
 [Omówienie](../../docs/framework/get-started/overview.md)
