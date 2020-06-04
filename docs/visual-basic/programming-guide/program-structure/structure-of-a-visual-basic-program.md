---
title: Struktura programu Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], Visual Basic
- program structure [Visual Basic], Visual Basic
- procedures [Visual Basic], structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
ms.openlocfilehash: dc6b38d78f02a42c8e7cc2aa964e9f3f74996f44
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408767"
---
# <a name="structure-of-a-visual-basic-program"></a>Struktura programu Visual Basic
Program Visual Basic jest zbudowany na podstawie standardowych bloków konstrukcyjnych. *Rozwiązanie* składa się z jednego lub większej liczby projektów. *Projekt* z kolei może zawierać jeden lub więcej zestawów. Każdy *zestaw* jest kompilowany z co najmniej jednego pliku źródłowego. *Plik źródłowy* zawiera definicje i implementacje klas, struktur, modułów i interfejsów, które ostatecznie zawierają cały kod.  
  
 Aby uzyskać więcej informacji na temat tych bloków konstrukcyjnych programu Visual Basic, zobacz [rozwiązania i projekty](/visualstudio/ide/solutions-and-projects-in-visual-studio) i [zestawy w programie .NET](../../../standard/assembly/index.md).  
  
## <a name="file-level-programming-elements"></a>Elementy programistyczne na poziomie plików  
 Gdy uruchamiasz projekt lub plik i otworzysz Edytor kodu, zobaczysz kod już na miejscu i w odpowiedniej kolejności. Każdy zapisany kod powinien być zgodny z następującą sekwencją:  
  
1. `Option`zatwierdzeni  
  
2. `Imports`zatwierdzeni  
  
3. `Namespace`instrukcje i elementy na poziomie przestrzeni nazw  
  
 Jeśli wprowadzasz instrukcje w innej kolejności, mogą wystąpić błędy kompilacji.  
  
 Program może również zawierać instrukcje kompilacji warunkowej. Można przeplatać je w pliku źródłowym między instrukcjami z poprzedniej sekwencji.  
  
### <a name="option-statements"></a>Instrukcje dotyczące opcji  
 `Option`instrukcje określają reguły podstaw dla kolejnego kodu, co pomaga zapobiegać błędom składni i logiki. [Instrukcja Explicit Option](../../language-reference/statements/option-explicit-statement.md) zapewnia, że wszystkie zmienne są zadeklarowane i sprawdzane poprawnie, co skraca czas debugowania. [Instrukcja Option Strict](../../language-reference/statements/option-strict-statement.md) pomaga zminimalizować błędy logiki i utratę danych, które mogą wystąpić podczas pracy między zmiennymi różnych typów danych. [Instrukcja Compare](../../language-reference/statements/option-compare-statement.md) określa sposób, w jaki ciągi są porównywane ze sobą, na podstawie ich `Binary` lub `Text` wartości.  
  
### <a name="imports-statements"></a>Importuje instrukcje  
 Można dołączyć [instrukcję Imports (przestrzeń nazw i typ platformy .NET)](../../language-reference/statements/imports-statement-net-namespace-and-type.md) do importowania nazw zdefiniowanych poza projektem. `Imports`Instrukcja umożliwia kod odwołujący się do klas i innych typów zdefiniowanych w zaimportowanym obszarze nazw bez konieczności kwalifikowania się do nich. W razie potrzeby można użyć dowolnej liczby `Imports` instrukcji. Aby uzyskać więcej informacji, zobacz [odwołania i instrukcje Imports](references-and-the-imports-statement.md).  
  
### <a name="namespace-statements"></a>Instrukcje przestrzeni nazw  
 Przestrzenie nazw ułatwiają organizowanie i klasyfikowanie elementów programistycznych w celu ułatwienia grupowania i uzyskiwania dostępu. Za pomocą [instrukcji Namespace](../../language-reference/statements/namespace-statement.md) można sklasyfikować poniższe instrukcje w ramach konkretnego obszaru nazw. Aby uzyskać więcej informacji, zobacz [przestrzenie nazw w Visual Basic](namespaces.md).  
  
### <a name="conditional-compilation-statements"></a>Instrukcje kompilacji warunkowej  
 Instrukcje kompilacji warunkowej mogą pojawiać się niemal w dowolnym miejscu w pliku źródłowym. Powodują, że części kodu mają być dołączone lub wykluczone w czasie kompilacji w zależności od określonych warunków. Można ich również używać do debugowania aplikacji, ponieważ kod warunkowy jest uruchamiany tylko w trybie debugowania. Aby uzyskać więcej informacji, zobacz [Kompilacja warunkowa](conditional-compilation.md).  
  
## <a name="namespace-level-programming-elements"></a>Elementy programistyczne na poziomie przestrzeni nazw  
 Klasy, struktury i moduły zawierają cały kod w pliku źródłowym. Są to elementy na *poziomie przestrzeni nazw* , które mogą być wyświetlane w przestrzeni nazw lub na poziomie pliku źródłowego. Posiadają deklaracje wszystkich innych elementów programistycznych. Interfejsy, które definiują podpisy elementów, ale nie zapewniają implementacji, są również wyświetlane na poziomie modułu. Więcej informacji o elementach poziomu modułu znajduje się w następujących tematach:  
  
- [Class, instrukcja](../../language-reference/statements/class-statement.md)  
  
- [Structure — Instrukcja](../../language-reference/statements/structure-statement.md)  
  
- [Module — Instrukcja](../../language-reference/statements/module-statement.md)  
  
- [Interface, instrukcja](../../language-reference/statements/interface-statement.md)  
  
 Elementy danych na poziomie przestrzeni nazw to wyliczenia i Delegaty.  
  
## <a name="module-level-programming-elements"></a>Elementy programowania na poziomie modułu  
 Procedury, operatory, właściwości i zdarzenia są jedynymi elementami programistycznymi, które mogą przechowywać kod wykonywalny (instrukcje wykonujące akcje w czasie wykonywania). Są to elementy programu na *poziomie modułu* . Więcej informacji o elementach poziomu procedury znajduje się w następujących tematach:  
  
- [Function, instrukcja](../../language-reference/statements/function-statement.md)  
  
- [Sub, instrukcja](../../language-reference/statements/sub-statement.md)  
  
- [Declare — Instrukcja](../../language-reference/statements/declare-statement.md)  
  
- [Operator — Instrukcja](../../language-reference/statements/operator-statement.md)  
  
- [Property — Instrukcja](../../language-reference/statements/property-statement.md)  
  
- [Event — Instrukcja](../../language-reference/statements/event-statement.md)  
  
 Elementy danych na poziomie modułu to zmienne, stałe, wyliczenia i Delegaty.  
  
## <a name="procedure-level-programming-elements"></a>Elementy programistyczne na poziomie procedury  
 Większość zawartości elementów *poziomu procedury* są instrukcje wykonywalne, które stanowią kod czasu wykonywania programu. Cały kod wykonywalny musi znajdować się w niektórych procedurach (,,,,, `Function` `Sub` ,, `Operator` `Get` `Set` `AddHandler` `RemoveHandler` `RaiseEvent` ). Aby uzyskać więcej informacji, zobacz [instrukcje](../language-features/statements.md).  
  
 Elementy danych na poziomie procedury są ograniczone do zmiennych lokalnych i stałych.  
  
## <a name="the-main-procedure"></a>Główna procedura  
 `Main`Procedura to pierwszy kod do uruchomienia, gdy aplikacja została załadowana. `Main`służy jako punkt początkowy i ogólna kontrola dla aplikacji. Istnieją cztery różne odmiany `Main` :  
  
- `Sub Main()`  
  
- `Sub Main(ByVal cmdArgs() As String)`  
  
- `Function Main() As Integer`  
  
- `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 Najbardziej powszechną odmianą tej procedury jest `Sub Main()` . Aby uzyskać więcej informacji, zobacz [Main procedur w Visual Basic](main-procedure.md).  
  
## <a name="see-also"></a>Zobacz też

- [Procedura główna w Visual Basic](main-procedure.md)
- [Visual Basic — Konwencje nazewnictwa](naming-conventions.md)
- [Ograniczenia Visual Basic](limitations.md)
