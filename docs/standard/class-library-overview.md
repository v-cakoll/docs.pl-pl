---
title: Przegląd biblioteki klas programu .NET
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acc51287a8c670da63d0ec421aa232864ea91c2b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185852"
---
# <a name="net-class-library-overview"></a>Przegląd biblioteki klas programu .NET

Implementacje platformy .NET zawierają klasy, interfejsy, delegaty i typów wartości, które przyspiesza i zoptymalizować proces tworzenia aplikacji oraz zapewnia dostęp do funkcji systemu. W celu ułatwienia współdziałanie między językami, większość typów .NET są zgodne ze specyfikacją CLS i w związku z tym można używać z dowolnego języka programowania, w których kompilator jest zgodny z common language specification (CLS).  
  
 Typy .NET to podstawę, na które .NET są tworzone aplikacje, składników i formantów. Implementacje platformy .NET zawierają typy, które wykonują następujące funkcje:  
  
-   Reprezentuje podstawowych typów danych i wyjątki.  
  
-   Hermetyzuj struktur danych.  
  
-   Operacje We/Wy.  
  
-   Uzyskiwanie dostępu do informacji o typach załadowane.  
  
-   Wywołaj kontrolę bezpieczeństwa .NET Framework.  
  
-   Zapewnia dostęp do danych, rozbudowane GUI po stronie klienta i kontrolowane przez serwer, po stronie klienta graficznego interfejsu użytkownika.  
  
 .NET zapewnia bogaty zestaw interfejsów, a także abstrakcyjne i konkretnych klas (nieabstrakcyjna). Możesz używać konkretnych klas, ponieważ jest lub w wielu przypadkach, dziedziczyć po ich własnych klas. Aby użyć funkcjonalności interfejsu, możesz utworzyć klasę, która implementuje interfejs lub wyprowadzić klasę z jednej z klas platformy .NET, które implementuje interfejs.  
  
## <a name="naming-conventions"></a>Konwencje nazewnictwa

 Typy .NET wykorzystują schemat nazewnictwa kropka składni, która connotes hierarchii. Ta technika grupy powiązanych typów w przestrzeni nazw, aby mogą być przeszukiwane i łatwiej odwoływać. Pierwsza część imię i nazwisko — maksymalnie kropki (.) po prawej stronie — jest nazwą przestrzeni nazw. Ostatnia część nazwy jest nazwą typu. Na przykład `System.Collections.Generic.List<T>` reprezentuje `List<T>` typ, który należy do `System.Collections.Generic` przestrzeni nazw. Typy w <xref:System.Collections.Generic> może służyć do pracy z kolekcji ogólnych.  
  
 Ten schemat nazewnictwa ułatwia deweloperom biblioteki rozszerzanie [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] utworzyć hierarchiczne grupy typów i nazwij je w sposób spójny, zawierającego wiele użytecznych informacji. Umożliwia także typy można jednoznacznie zidentyfikować przez ich pełną nazwę (czyli według nazwy przestrzeni nazw i typ), co uniemożliwia Kolizje nazw typu. Deweloperzy biblioteki powinny używać następującej konwencji, podczas tworzenia nazwy dla ich przestrzenie nazw:  
  
 *CompanyName*.*TechnologyName*  
  
 Na przykład, przestrzeń nazw `Microsoft.Word` odpowiada niniejszych wytycznych.  
  
 Korzystanie z wzorców nazewnictwa do grupy powiązanych typów w przestrzeni nazw jest bardzo przydatny sposób tworzenia i zarządzania dokumentami bibliotek klas. Jednak ten schemat nazewnictwa nie ma wpływu na widoczność, dostęp do elementu członkowskiego, dziedziczenie, zabezpieczeń lub powiązania. Przestrzeń nazw można podzielić na partycje w wielu zestawach i pojedynczy zestaw może zawierać typy z wielu obszary nazw. Zestaw zawiera formalne struktury przechowywania wersji, wdrażania, zabezpieczeń, ładowania i wgląd w środowisko uruchomieniowe języka wspólnego.  
  
 Aby uzyskać więcej informacji na temat nazw przestrzenie nazw i typ, zobacz [Wspólny System typów](../../docs/standard/base-types/common-type-system.md).  
  
## <a name="system-namespace"></a>Przestrzeń nazw systemu

 <xref:System> Przestrzeń nazw jest przestrzeń nazw korzenia dla podstawowych typów na platformie .NET. Ta przestrzeń nazw zawiera klasy reprezentujące podstawowe typy danych używany przez wszystkie aplikacje: <xref:System.Object> (główny hierarchii dziedziczenia), <xref:System.Byte>, <xref:System.Char>, <xref:System.Array>, <xref:System.Int32>, <xref:System.String>i tak dalej. Wiele z tych typów odnoszą się do typów danych pierwotnych, które używa języka programowania. Podczas pisania kodu za pomocą typów programu .NET Framework, można użyć danego języka odpowiednich słów kluczowych podczas .NET Framework jest oczekiwany typ danych podstawowych.  
  
 Poniższa tabela zawiera listę typów podstawowych, że .NET dostarcza, krótko opisano każdy typ i oznacza odpowiedni typ w języku Visual Basic, C#, C++ i F #.  
  
|Kategoria|Nazwa klasy|Opis|Typ danych w języku Visual Basic|Typ danych w języku C#|C + +/ interfejsu wiersza polecenia — typ danych|Typów danych języka F #|  
|--------------|----------------|-----------------|----------------------------|-------------------|---------------------|-----------------------|  
|Liczba całkowita|<xref:System.Byte>|8-bitowa liczba całkowita bez znaku.|**Byte**|**byte**|**unsigned char**|**byte**|  
||<xref:System.SByte>|8-bitową całkowita.<br /><br /> Niezgodne ze specyfikacją CLS.|**SByte**|**sbyte**|**char**<br /> —lub—<br /> **podpisana** **char**|**sbyte**|  
||<xref:System.Int16>|Całkowita 16-bitowych.|**Short**|**short**|**short**|**int16**|  
||<xref:System.Int32>|Całkowita 32-bitowych.|**Integer**|**int**|**int**<br /><br /> —lub—<br /><br /> **long**|**int**|  
||<xref:System.Int64>|Całkowita 64-bitowych.|**Long**|**long**|**__int64**|**int64**|  
||<xref:System.UInt16>|16-bitowa liczba całkowita bez znaku.<br /><br /> Niezgodne ze specyfikacją CLS.|**UShort**|**ushort**|**short bez znaku**|**uint16**|  
||<xref:System.UInt32>|32-bitowa liczba całkowita bez znaku.<br /><br /> Niezgodne ze specyfikacją CLS.|**UInteger**|**uint**|**unsigned int**<br /> —lub—<br /> **unsigned long**|**uint32**|  
||<xref:System.UInt64>|64-bitowej nieoznaczonej liczby całkowitej.<br /><br /> Niezgodne ze specyfikacją CLS.|**ULong**|**ulong**|**__int64 bez znaku**|**uint64**|  
|Liczba zmiennoprzecinkowa|<xref:System.Single>|Liczba zmiennoprzecinkowa (32-bitowy) pojedynczej precyzji.|**Single**|**float**|**float**|**float32**</br> lub</br>**single**|  
||<xref:System.Double>|Liczba zmiennoprzecinkowa (64-bitowy) podwójnej precyzji.|**Double**|**double**|**double**|**float**</br> lub </br> **double**|  
|Logiczne|<xref:System.Boolean>|Wartość logiczna (true lub false).|**Boolean**|**bool**|**bool**|**bool**|  
|Inne|<xref:System.Char>|Znak Unicode (16-bitowe).|**Char**|**char**|**wchar_t**|**char**|  
||<xref:System.Decimal>|Wartość dziesiętna (128-bitowe).|**Decimal**|**decimal**|**Decimal**|**decimal**|  
||<xref:System.IntPtr>|Liczba całkowita ze znakiem której rozmiar jest zależna od podstawowej platformy (32-bitową wartość na platformie 32-bitowe) i 64-bitowych wartości na platformie 64-bitowej.|**Pola IntPtr**<br /><br /> Brak typu wbudowanego.|**Pola IntPtr**<br /><br /> Brak typu wbudowanego.|**Pola IntPtr**<br /><br /> Brak typu wbudowanego.|**unativeint —**|  
||<xref:System.UIntPtr>|Liczbą całkowitą bez znaku, którego rozmiar jest zależna od podstawowej platformy (32-bitową wartość na platformie 32-bitowe) i 64-bitowych wartości na platformie 64-bitowej.<br /><br /> Niezgodne ze specyfikacją CLS.|**UIntPtr**<br /><br /> Brak typu wbudowanego.|**UIntPtr**<br /><br /> Brak typu wbudowanego.|**UIntPtr**<br /><br /> Brak typu wbudowanego.|**unativeint —**|  
||<xref:System.Object>|Katalog główny hierarchii obiektów.|**obiekt**|**object**|**Object ^**|**obj**|  
||<xref:System.String>|Niezmienny, o stałej długości ciągu znaków Unicode.|**Ciąg**|**string**|**String ^**|**string**|  
  
 Oprócz podstawowe typy danych <xref:System> przestrzeń nazw zawiera klasy ponad 100, począwszy od klas, które obsługi wyjątków do klas, które zajmują się podstawowe koncepcje środowiska uruchomieniowego, takich jak domeny aplikacji i moduł odśmiecania pamięci. <xref:System> Przestrzeń nazw zawiera także wiele nazw drugiego poziomu.  
  
 Aby uzyskać więcej informacji na temat przestrzenie nazw, należy użyć [przeglądarka interfejsu API .NET](https://docs.microsoft.com/dotnet/api) do przeglądania biblioteki klas programu .NET. Dokumentacja referencyjna interfejsu API zawiera dokumentację w każdej przestrzeni nazw, jego typy i wszystkich ich elementów członkowskich.  
  
## <a name="see-also"></a>Zobacz także

- [System typu wspólnego](../../docs/standard/base-types/common-type-system.md)  
- [Przeglądarka interfejsu API .NET](https://docs.microsoft.com/dotnet/api)  
- [Omówienie](../../docs/framework/get-started/overview.md)
