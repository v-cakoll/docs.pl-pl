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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400485"
---
# <a name="net-class-library-overview"></a>Omówienie biblioteki klas .NET

Implementacje .NET obejmują klasy, interfejsy, delegatów i typy wartości, które przyspieszają i optymalizują proces tworzenia i zapewniają dostęp do funkcji systemu. Aby ułatwić współdziałanie między językami, większość typów .NET jest zgodna ze specyfikacją CLS i dlatego może być używana z dowolnego języka programowania, którego kompilator jest zgodny ze specyfikacją języka wspólnego (CLS).  
  
 Typy .NET są podstawą, na której są tworzone aplikacje,NET, składniki i formanty. Implementacje .NET obejmują typy, które wykonują następujące funkcje:  
  
- Reprezentują typy danych podstawowych i wyjątki.  
  
- Hermetyzować struktury danych.  
  
- Wykonaj we/wy.  
  
- Dostęp do informacji o załadowanych typach.  
  
- Wywołanie kontroli zabezpieczeń .NET Framework.  
  
- Zapewnij dostęp do danych, rozbudowany interfejs graficzny po stronie klienta i interfejs graficzny sterowany przez serwer.  
  
 .NET udostępnia bogaty zestaw interfejsów, a także klasy abstrakcyjne i konkretne (nieabstrakcyjne). Można użyć konkretnych klas, jak jest lub, w wielu przypadkach, czerpać własne klasy z nich. Aby użyć funkcji interfejsu, można utworzyć klasę, która implementuje interfejs lub wyprowadzić klasę z jednej z klas .NET, która implementuje interfejs.  
  
## <a name="naming-conventions"></a>Konwencje nazewnictwa

 Typy .NET używają schematu nazewnictwa składni kropki, który oznacza hierarchię. Ta technika grupuje powiązane typy w przestrzenie nazw, dzięki czemu można je łatwiej przeszukiwać i odwoływać się do niej. Pierwsza część pełnej nazwy — aż do prawej kropki — to nazwa obszaru nazw. Ostatnia część nazwy to nazwa typu. Na przykład `System.Collections.Generic.List<T>` reprezentuje `List<T>` typ, który należy `System.Collections.Generic` do obszaru nazw. Typy w <xref:System.Collections.Generic> może służyć do pracy z kolekcji ogólnych.  
  
 Ten schemat nazewnictwa ułatwia deweloperom biblioteki rozszerzanie platformy .NET Framework do tworzenia hierarchicznych grup typów i nadawanie im nazw w spójny, informacyjny sposób. Umożliwia również typy, które mają być jednoznacznie identyfikowane przez ich pełną nazwę (to znaczy przez ich obszar nazw i nazwę typu), co zapobiega kolizji nazw typów. Deweloperzy biblioteki powinni używać następującej konwencji podczas tworzenia nazw dla swoich obszarów nazw:  
  
 *Nazwa firmy*. *Nazwa technologii*  
  
 Na przykład obszar `Microsoft.Word` nazw jest zgodny z niniejszą wytyczną.  
  
 Użycie wzorców nazewnictwa do grupowania powiązanych typów w przestrzenie nazw jest bardzo przydatnym sposobem tworzenia i dokumentowania bibliotek klas. Jednak ten schemat nazewnictwa nie ma wpływu na widoczność, dostęp do elementów członkowskich, dziedziczenie, zabezpieczenia lub powiązanie. Obszar nazw może być podzielony na partycje w wielu zestawach, a pojedynczy zestaw może zawierać typy z wielu obszarów nazw. Zestaw zapewnia formalną strukturę do wersji, wdrażania, zabezpieczeń, ładowania i widoczności w czasie wykonywania języka wspólnego.  
  
 Aby uzyskać więcej informacji na temat obszarów nazw i nazw typów, zobacz [System typów wspólnych](../../docs/standard/base-types/common-type-system.md).  
  
## <a name="system-namespace"></a>Przestrzeń nazw systemu

 Obszar <xref:System> nazw jest głównym obszarem nazw dla typów podstawowych w .NET. Ten obszar nazw zawiera klasy reprezentujące podstawowe typy <xref:System.Object> danych używane przez wszystkie <xref:System.Byte> <xref:System.Char>aplikacje: (katalog główny hierarchii dziedziczenia), , , <xref:System.Array>, <xref:System.Int32>, <xref:System.String>i tak dalej. Wiele z tych typów odpowiada pierwotnym typom danych, których używa język programowania. Podczas pisania kodu przy użyciu typów .NET Framework, można użyć odpowiedniego słowa kluczowego języka, gdy oczekuje się podstawowego typu danych .NET Framework.  
  
 W poniższej tabeli wymieniono typy podstawowe, które jest dostarczana przez program .NET, krótko opisuje każdy typ i wskazuje odpowiedni typ w językach Visual Basic, C#, C++ i F#.  
  
|Kategoria|Nazwa klasy|Opis|Typ danych języka Visual Basic|Typ danych języka C#|Typ danych C++/CLI|Typ danych F#|  
|--------------|----------------|-----------------|----------------------------|-------------------|---------------------|-----------------------|  
|Liczba całkowita|<xref:System.Byte>|8-bitowa liczba całkowita bez znaku.|**Byte**|**Bajtów**|**unsigned char**|**Bajtów**|  
||<xref:System.SByte>|8-bitowa liczba całkowita podpisana.<br /><br /> Nie zgodny ze specyfikacją CLS.|**Sbyte**|**Sbyte**|**char**<br /> — lub —<br /> **podpisany** **znak**|**Sbyte**|  
||<xref:System.Int16>|16-bitowa liczba całkowita podpisana.|**Krótki**|**short**|**short**|**int16 ( int16 )**|  
||<xref:System.Int32>|32-bitowa liczba całkowita podpisana.|**Liczba całkowita**|**int**|**int**<br /><br /> — lub —<br /><br /> **long**|**int**|  
||<xref:System.Int64>|64-bitowa liczba całkowita podpisana.|**Długi**|**long**|**__int64**|**int64**|  
||<xref:System.UInt16>|16-bitowa liczba całkowita bez znaku.<br /><br /> Nie zgodny ze specyfikacją CLS.|**Ushort**|**ushort**|**unsigned short**|**uint16 ( uint16 )**|  
||<xref:System.UInt32>|32-bitowa liczba całkowita bez znaku.<br /><br /> Nie zgodny ze specyfikacją CLS.|**Uinteger**|**Uint**|**unsigned int**<br /> — lub —<br /> **unsigned long**|**uint32 (uint32)**|  
||<xref:System.UInt64>|64-bitowa liczba całkowita bez znaku.<br /><br /> Nie zgodny ze specyfikacją CLS.|**Ulong**|**ulong**|**niepodpisane __int64**|**uint64 ( uint64 )**|  
|Liczba zmiennoprzecinkowa|<xref:System.Single>|Jednolita (32-bitowa) liczba zmiennoprzecinkowych.|**Single**|**float**|**float**|**pływak32**<br> lub<br>**Pojedynczy**|  
||<xref:System.Double>|Dwulita precyzja (64-bitowa) liczba zmiennoprzecinkowych.|**Podwójne**|**double**|**double**|**float**<br> lub <br> **double**|  
|Logiczny|<xref:System.Boolean>|Wartość logiczna (prawda lub fałsz).|**Wartość logiczna**|**bool**|**bool**|**bool**|  
|Inne|<xref:System.Char>|Znak Unicode (16-bitowy).|**Char**|**char**|**wchar_t**|**char**|  
||<xref:System.Decimal>|Wartość dziesiętna (128-bitowa).|**Dziesiętnych**|**decimal**|**Dziesiętnych**|**decimal**|  
||<xref:System.IntPtr>|Podpisana liczba całkowita, której rozmiar zależy od platformy bazowej (wartość 32-bitowa na platformie 32-bitowej i wartość 64-bitowa na platformie 64-bitowej).|**Intptr**<br /><br /> Brak wbudowanego typu.|**Intptr**<br /><br /> Brak wbudowanego typu.|**Intptr**<br /><br /> Brak wbudowanego typu.|**unativeint (unativeint)**|  
||<xref:System.UIntPtr>|Niepodpisana liczba całkowita, której rozmiar zależy od platformy źródłowej (wartość 32-bitowa na platformie 32-bitowej i wartość 64-bitowa na platformie 64-bitowej).<br /><br /> Nie zgodny ze specyfikacją CLS.|**Uintptr**<br /><br /> Brak wbudowanego typu.|**Uintptr**<br /><br /> Brak wbudowanego typu.|**Uintptr**<br /><br /> Brak wbudowanego typu.|**unativeint (unativeint)**|  
||<xref:System.Object>|Katalog główny hierarchii obiektów.|**Obiektu**|**obiekt**|**Obiekt^**|**Obj**|  
||<xref:System.String>|Niezmienny ciąg znaków Unicode o stałej długości.|**Ciąg**|**ciąg**|**Ciąg^**|**ciąg**|  
  
 Oprócz podstawowych typów danych obszar <xref:System> nazw zawiera ponad 100 klas, począwszy od klas, które obsługują wyjątki do klas, które zajmują się podstawowych pojęć czasu wykonywania, takich jak domeny aplikacji i moduł zbierający elementy bezużyteczne. Obszar <xref:System> nazw zawiera również wiele przestrzeni nazw drugiego poziomu.  
  
 Aby uzyskać więcej informacji o przestrzeniach nazw, użyj [przeglądarki interfejsu API .NET,](https://docs.microsoft.com/dotnet/api) aby przeglądać bibliotekę klas .NET. Dokumentacja referencyjna interfejsu API zawiera dokumentację dotyczącą każdego obszaru nazw, jego typów i każdego z ich członków.  
  
## <a name="see-also"></a>Zobacz też

- [System typu wspólnego](../../docs/standard/base-types/common-type-system.md)
- [Przeglądarka interfejsu API .NET](../../api/index.md)
- [Przegląd](../../docs/framework/get-started/overview.md)
