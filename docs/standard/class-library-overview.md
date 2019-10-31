---
title: Omówienie biblioteki klas .NET
ms.date: 02/08/2018
ms.technology: dotnet-standard
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
ms.openlocfilehash: 596c0fd8fec8f59d977f1db445f9000df23ad5ce
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132846"
---
# <a name="net-class-library-overview"></a>Omówienie biblioteki klas .NET

Implementacje platformy .NET obejmują klasy, interfejsy, Delegaty i typy wartości, które przyspieszają i optymalizują proces tworzenia i zapewniają dostęp do funkcji systemu. Aby ułatwić współdziałanie między językami, większość typów .NET jest zgodna ze specyfikacją CLS i dlatego może być używana z dowolnego języka programowania, którego kompilator jest zgodny ze specyfikacją języka wspólnego (CLS).  
  
 Typy .NET są podstawą, w której są kompilowane aplikacje, składniki i formanty platformy .NET. Implementacje programu .NET obejmują typy, które wykonują następujące funkcje:  
  
- Reprezentuje podstawowe typy danych i wyjątki.  
  
- Hermetyzuj struktury danych.  
  
- Wykonywanie operacji we/wy.  
  
- Uzyskaj dostęp do informacji o załadowanych typach.  
  
- Wywołaj .NET Framework sprawdzenia zabezpieczeń.  
  
- Zapewnianie dostępu do danych, rozbudowanego interfejsu GUI po stronie klienta oraz interfejsu GUI po stronie klienta.  
  
 Platforma .NET oferuje bogaty zestaw interfejsów, a także abstrakcyjne i specyficzne klasy (nieabstrakcyjne). Klas konkretnych można użyć jako lub, w wielu przypadkach, należy utworzyć własne klasy z nich. Aby użyć funkcji interfejsu, można utworzyć klasę, która implementuje interfejs lub dziedziczyć klasy z jednej z klas .NET, które implementują interfejs.  
  
## <a name="naming-conventions"></a>Konwencje nazewnictwa

 Typy .NET używają schematu nazewnictwa składni z kropką, który oznacza hierarchię. Ta technika grupuje powiązane typy w przestrzeni nazw, dzięki czemu mogą być przeszukiwane i łatwiejsze do przywoływane. Pierwsza część pełnej nazwy — do skrajnej prawej kropki — to nazwa przestrzeni nazw. Ostatnia część nazwy jest nazwą typu. Na przykład `System.Collections.Generic.List<T>` reprezentuje typ `List<T>`, który należy do przestrzeni nazw `System.Collections.Generic`. Typy w <xref:System.Collections.Generic> mogą służyć do pracy z kolekcjami ogólnymi.  
  
 Ten schemat nazewnictwa ułatwia deweloperom biblioteki rozszerzanie .NET Framework w celu tworzenia hierarchicznych grup typów i nazywania ich w spójny, informacyjny sposób. Umożliwia także jednoznaczne zidentyfikowanie typów według ich pełnej nazwy (czyli według ich przestrzeni nazw i nazwy typu), co zapobiega kolizji nazw typów. Deweloperzy biblioteki powinni używać następującej konwencji podczas tworzenia nazw dla ich przestrzeni nazw:  
  
 *NazwaFirmy*. Nr *technologii*  
  
 Na przykład przestrzeń nazw `Microsoft.Word` jest zgodna z tymi wskazówkami.  
  
 Użycie wzorców nazewnictwa do grupowania powiązanych typów w przestrzeni nazw to bardzo użyteczny sposób kompilowania i dokumentowania bibliotek klas. Jednak ten schemat nazewnictwa nie ma wpływu na widoczność, dostęp do elementu członkowskiego, dziedziczenie, zabezpieczenia ani powiązanie. Przestrzeń nazw może być partycjonowana w wielu zestawach, a pojedynczy zestaw może zawierać typy z wielu przestrzeni nazw. Zestaw zawiera formalną strukturę dla wersji, wdrożenia, zabezpieczeń, ładowania i widoczności w środowisku uruchomieniowym języka wspólnego.  
  
 Aby uzyskać więcej informacji na temat przestrzeni nazw i nazw typów, zobacz [Common Type System](../../docs/standard/base-types/common-type-system.md).  
  
## <a name="system-namespace"></a>Przestrzeń nazw systemu

 Przestrzeń nazw <xref:System> to główna przestrzeń nazw dla podstawowych typów w programie .NET. Ta przestrzeń nazw zawiera klasy reprezentujące podstawowe typy danych używane przez wszystkie aplikacje: <xref:System.Object> (katalog główny hierarchii dziedziczenia), <xref:System.Byte>, <xref:System.Char>, <xref:System.Array>, <xref:System.Int32>, <xref:System.String>i tak dalej. Wiele z tych typów odpowiada typom danych pierwotnych używanym przez język programowania. Podczas pisania kodu przy użyciu typów .NET Framework, można użyć słowa kluczowego odpowiedniego dla danego języka, gdy oczekiwany jest .NET Framework podstawowy typ danych.  
  
 Poniższa tabela zawiera listę typów podstawowych, które są używane przez platformę .NET, krótko opisuje każdy typ i wskazuje odpowiedni typ C#w C++Visual Basic, F#,, i.  
  
|Kategoria|Nazwa klasy|Opis|Typ danych Visual Basic|C#Typ danych|C++/CLI — typ danych|F#Typ danych|  
|--------------|----------------|-----------------|----------------------------|-------------------|---------------------|-----------------------|  
|Liczba całkowita|<xref:System.Byte>|8-bitowa liczba całkowita bez znaku.|**Bajc**|**byte**|**znak bez znaku**|**byte**|  
||<xref:System.SByte>|8-bitowa liczba całkowita ze znakiem.<br /><br /> Niezgodny ze specyfikacją CLS.|**SByte**|**sbyte**|**char**<br /> —lub—<br /> **znak** ze znakiem|**sbyte**|  
||<xref:System.Int16>|16-bitowa liczba całkowita ze znakiem.|**Wybierak**|**short**|**short**|**Int16**|  
||<xref:System.Int32>|32-bitowa liczba całkowita ze znakiem.|**Całkowitą**|**int**|**int**<br /><br /> —lub—<br /><br /> **long**|**int**|  
||<xref:System.Int64>|64-bitowa liczba całkowita ze znakiem.|**Długo**|**long**|**__int64**|**Int64**|  
||<xref:System.UInt16>|16-bitowa liczba całkowita bez znaku.<br /><br /> Niezgodny ze specyfikacją CLS.|**UShort**|**ushort**|**bez znaku Short**|**UInt16**|  
||<xref:System.UInt32>|32-bitowa liczba całkowita bez znaku.<br /><br /> Niezgodny ze specyfikacją CLS.|**UInteger —**|**uint**|**niepodpisany int**<br /> —lub—<br /> **bez znaku**|**równ**|  
||<xref:System.UInt64>|64-bitowa liczba całkowita bez znaku.<br /><br /> Niezgodny ze specyfikacją CLS.|**ULong**|**ulong**|**__int64 bez znaku**|**UInt64**|  
|Liczba zmiennoprzecinkowa|<xref:System.Single>|Liczba zmiennoprzecinkowa o pojedynczej precyzji (32-bitowej).|**Wiersz**|**float**|**float**|**float32**<br> lub<br>**single**|  
||<xref:System.Double>|Liczba zmiennoprzecinkowa o podwójnej precyzji (64-bitowej).|**Double**|**double**|**double**|**float**<br> lub <br> **double**|  
|logicznej|<xref:System.Boolean>|Wartość logiczna (true lub false).|**Typu**|**bool**|**bool**|**bool**|  
|Inne|<xref:System.Char>|Znak Unicode (16-bitowy).|**Delikatn**|**char**|**wchar_t**|**char**|  
||<xref:System.Decimal>|Wartość dziesiętna (128-bitowa).|**Dokładności**|**decimal**|**Dokładności**|**decimal**|  
||<xref:System.IntPtr>|Liczba całkowita ze znakiem, której rozmiar zależy od podstawowej platformy (wartość 32-bitowa na platformie 32-bitowej i 64-bitowej na platformie 64-bitowej).|**IntPtr**<br /><br /> Brak typu wbudowanego.|**IntPtr**<br /><br /> Brak typu wbudowanego.|**IntPtr**<br /><br /> Brak typu wbudowanego.|**unativeint —**|  
||<xref:System.UIntPtr>|Liczba całkowita bez znaku, której rozmiar zależy od podstawowej platformy (wartość 32-bitowa na platformie 32-bitowej i 64-bitowej wartości na platformie 64-bitowej).<br /><br /> Niezgodny ze specyfikacją CLS.|**UIntPtr**<br /><br /> Brak typu wbudowanego.|**UIntPtr**<br /><br /> Brak typu wbudowanego.|**UIntPtr**<br /><br /> Brak typu wbudowanego.|**unativeint —**|  
||<xref:System.Object>|Katalog główny hierarchii obiektów.|**Stream**|**object**|**Obiekt ^**|**obiektów**|  
||<xref:System.String>|Niezmienny ciąg o stałej długości znaków Unicode.|**Ciąg**|**string**|**Ciąg ^**|**string**|  
  
 Oprócz podstawowych typów danych, przestrzeń nazw <xref:System> zawiera ponad 100 klas, od klas, które obsługują wyjątki dla klas, które obejmują podstawowe koncepcje środowiska uruchomieniowego, takie jak domeny aplikacji i moduł wyrzucania elementów bezużytecznych. Przestrzeń nazw <xref:System> również zawiera wiele przestrzeni nazw drugiego poziomu.  
  
 Aby uzyskać więcej informacji na temat przestrzeni nazw, należy użyć [przeglądarki interfejsu API .NET](https://docs.microsoft.com/dotnet/api) do przeglądania biblioteki klas .NET. Dokumentacja dotycząca interfejsów API zawiera dokumentację dla każdej przestrzeni nazw, jej typów i każdego z nich.  
  
## <a name="see-also"></a>Zobacz także

- [System typu wspólnego](../../docs/standard/base-types/common-type-system.md)
- [Przeglądarka interfejsów API platformy .NET](../../api/index.md)
- [Omówienie](../../docs/framework/get-started/overview.md)
