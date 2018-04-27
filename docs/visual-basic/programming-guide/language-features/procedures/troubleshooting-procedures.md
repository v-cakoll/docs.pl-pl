---
title: Procedury rozwiązywania problemów (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- troubleshooting Visual Basic, procedures
- procedures [Visual Basic], troubleshooting
- Visual Basic code, procedures
- troubleshooting procedures
- procedures [Visual Basic], about procedures
ms.assetid: 525721e8-2e02-4f75-b5d8-6b893462cf2b
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7e54c965dc15131734be2c5bcfe04ad70292bf23
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="troubleshooting-procedures-visual-basic"></a>Procedury rozwiązywania problemów (Visual Basic)
Ta strona zawiera listę typowych problemów, które mogą wystąpić podczas pracy z procedury.  
  
## <a name="returning-an-array-type-from-a-function-procedure"></a>Zwracanie typem tablicy z procedury — funkcja  
 Jeśli `Function` procedury zwraca typ danych tablicy, nie można użyć `Function` Nazwa wartości mają być przechowywane w elementach tablicy. Jeśli użytkownik spróbuje to zrobić, kompilator zinterpretuje ją jako wywołanie `Function`. Poniższy przykład generuje błędy kompilatora.  
  
 `Function allOnes(ByVal n As Integer) As Integer()`  
  
 `For i As Integer = 1 To n - 1`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `allOnes(i) = 1`  
  
 `Next i`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `Return allOnes()`  
  
 `End Function`  
  
 Instrukcja `allOnes(i) = 1` generuje błąd kompilatora, ponieważ prawdopodobnie wywołać `allOnes` z nieprawidłowym argumentem niewłaściwy typ danych (pojedynczą `Integer` zamiast `Integer` tablicy). Instrukcja `Return allOnes()` generuje błąd kompilatora, ponieważ prawdopodobnie wywołać `allOnes` z żadnego argumentu.  
  
 **Poprawne podejście:** Aby móc modyfikować elementy w tablicy, która jest zwracana zdefiniować tablicę wewnętrzny jako zmiennej lokalnej. Poniższy przykład tworzy się bez błędów.  
  
 [!code-vb[VbVbcnProcedures#66](./codesnippet/VisualBasic/troubleshooting-procedures_1.vb)]  
  
## <a name="argument-not-being-modified-by-procedure-call"></a>Argument nie jest modyfikowany przez wywołanie procedury  
 Jeśli zamierzasz zezwolić procedury można zmienić elementu programistycznego bazowy argumentu w wywoływanym kodzie, trzeba przekazać go przez odwołanie. Ale procedury mogą uzyskiwać dostęp do elementów argument typu odwołania, nawet jeśli przekazywany przez wartość.  
  
-   **Bazowy zmiennej**. Umożliwia procedury zastąpić wartość zmiennej podstawowej samego elementu procedura musi deklarować parametr [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md). Ponadto kod wywołujący musi nie należy umieścić argument w nawiasach, ponieważ który przesłonić `ByRef` mechanizmu przekazywania.  
  
-   **Elementy typu odwołania**. Przy deklarowaniu parametru [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md), procedury nie można zmodyfikować podstawowej zmiennej elementu. Jednak jeśli wartością argumentu jest typem referencyjnym, procedury można zmodyfikować elementów członkowskich obiektu, który wskazuje, nawet jeśli nie można zastąpić wartość zmiennej. Na przykład jeśli argument jest zmienną tablicową, procedury nie można przypisać nowej tablicy do niego, ale można zmienić, co najmniej jeden z jego elementów. Zmienione elementy są widoczne w podstawowej zmiennej tablicy w wywoływanym kodzie.  
  
 W poniższym przykładzie zdefiniowano dwie procedury, które podejmują zmienną tablicową według wartości i które działają na swoich elementów. Procedura `increase` po prostu dodaje je do każdego elementu. Procedura `replace` przypisuje nową macierz do parametru `a()` , a następnie dodaje je do każdego elementu. Jednak ponowne przypisanie nie wpływa na podstawowe zmiennej tablicy w wywoływanym kodzie ponieważ `a()` zadeklarowano `ByVal`.  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/troubleshooting-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/troubleshooting-procedures_3.vb)]  
  
 Poniższy przykład wykonywania wywołań do `increase` i `replace`.  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/troubleshooting-procedures_4.vb)]  
  
 Pierwszy `MsgBox` wywołać Wyświetla "po increase(n): 11, 21, 31, 41". Ponieważ `n` jest typem referencyjnym `increase` można zmienić jej członków, nawet jeśli jest przekazywany `ByVal`.  
  
 Drugi `MsgBox` wywołać Wyświetla "po replace(n): 11, 21, 31, 41". Ponieważ `n` jest przekazywany `ByVal`, `replace` nie można zmodyfikować zmienną `n` przez przypisanie nowej tablicy. Gdy `replace` tworzy nowe wystąpienie tablicy `k` i przypisuje go do zmiennej lokalnej `a`, tym samym odwołanie do `n` przekazany przez wywołującego kodu. Gdy powoduje zwiększenie członków `a`, lokalnej tablicy `k` dotyczy.  
  
 **Poprawne podejście:** się zmodyfikować odpowiedniego elementu zmiennej sam przekazywany przez odwołanie. Poniższy przykład przedstawia zmiany w deklaracji `replace` który pozwala na zastępowanie jedną tablicę innym w wywoływanym kodzie.  
  
 [!code-vb[VbVbcnProcedures#64](./codesnippet/VisualBasic/troubleshooting-procedures_5.vb)]  
  
## <a name="unable-to-define-an-overload"></a>Nie można zdefiniować przeciążenia  
 Jeśli chcesz zdefiniować przeciążonego wersji procedury, musi użyć takiej samej nazwie, ale inny podpis. Jeśli kompilator nie rozróżnianie z deklaracji z przeciążenia o tej samej sygnaturze, zostanie wygenerowany błąd.  
  
 *Podpisu* procedury jest określany przez nazwę procedury i listy parametrów. Każdy przeciążenia musi mieć taką samą nazwę jak wszystkie inne przeciążenia, ale musi różnić się od wszystkich z nich w co najmniej jednym ze składników podpisu. Aby uzyskać więcej informacji, zobacz [przeciążanie procedury](./procedure-overloading.md).  
  
 Następujące elementy, mimo że odnoszą się do listy parametrów nie są składniki podpis procedury:  
  
-   Słowa kluczowe modyfikator procedury, takich jak `Public`, `Shared`, i `Static`  
  
-   Nazwy parametrów  
  
-   Słowa kluczowe modyfikator parametrów, takich jak `ByRef` i `Optional`  
  
-   Typ danych wartości zwracanej (z wyjątkiem operatora konwersji)  
  
 Procedury nie mogą przeciążać przez zróżnicowanie tylko co najmniej jeden z wymienionych elementów.  
  
 **Poprawne podejście:** możliwość definiowania przeciążenia procedury, muszą się różnić podpisu. Należy użyć tej samej nazwy, gdy trzeba zmieniać numer, kolejność lub typów danych parametrów. Procedury ogólne może się różnić z liczbą parametrów typu. W operator konwersji ([CType — funkcja](../../../../visual-basic/language-reference/functions/ctype-function.md)), może różnić się typ zwracany.  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>Przeciążenia rozdzielczość opcjonalne i ParamArray-argumenty  
 Jeśli są przeciążanie procedury z jednym lub kilkoma [opcjonalnie](../../../../visual-basic/language-reference/modifiers/optional.md) parametrów lub [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametru, możesz należy unikać duplikowania żadnego z *niejawne przeładowania*. Aby uzyskać informacje, zobacz [zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md).  
  
## <a name="calling-a-wrong-version-of-an-overloaded-procedure"></a>Wywoływanie procedury przeciążenia Nieprawidłowa wersja  
 Jeśli procedura ma kilka zastąpionej wersji, należy należy zapoznać się z ich listy parametrów i zrozumieć, jak Visual Basic rozpoznaje wywołania między przeciążeń. W przeciwnym razie można wywoływać przeciążenia innego niż zamierzone.  
  
 Po określeniu przeciążenia, które chcesz się połączyć, należy zachować ostrożność zgodna z poniższymi regułami:  
  
-   Podaj poprawną liczbę argumentów i we właściwej kolejności.  
  
-   Najlepiej argumentów ma dokładnie takich samych typach danych jako wartości odpowiadających im parametrów. W każdym przypadku typ danych argumentu musi poszerzyć niż jego odpowiadającego mu parametru. Dotyczy to nawet w przypadku [Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md) ustawioną `Off`. Jeśli przeciążenia wymaga żadnych zwężenia konwersji z listy argumentów, które przeciążenia nie jest uprawniony do wywołania.  
  
-   Podano argumenty, które wymagają rozszerzenia, aby ich typy danych jak najbliżej odpowiedni typ danych parametru. Po zaakceptowaniu przeciążenia dwóch lub więcej typów danych argumentu kompilator rozpoznaje wywołania do przeciążenia, które wymaga minimalnej liczbie rozszerzanie.  
  
 Można zmniejszyć ryzyko wystąpienia niezgodności typu danych przy użyciu [CType — funkcja](../../../../visual-basic/language-reference/functions/ctype-function.md) konwersji — słowo kluczowe podczas przygotowywania argumentów.  
  
### <a name="overload-resolution-failure"></a>Błąd rozpoznawania przeciążenia  
 Wywoływanie procedury przeciążenia, kompilator próbuje usunąć wszystkie oprócz jednego z przeciążeń. Jeśli próba powiedzie się, usuwa można wywołać tego przeciążenia. Jeśli eliminuje wszystkie przeciążenia lub nie można zmniejszyć przeciążeń kwalifikujących się do pojedynczego kandydujących, zostanie wygenerowany błąd.  
  
 Poniższy przykład przedstawia proces rozpoznawania przeciążenia.  
  
 [!code-vb[VbVbcnProcedures#62](./codesnippet/VisualBasic/troubleshooting-procedures_6.vb)]  
  
 [!code-vb[VbVbcnProcedures#63](./codesnippet/VisualBasic/troubleshooting-procedures_7.vb)]  
  
 W pierwszym wywołaniu kompilator eliminuje pierwszy przeciążenia, ponieważ typ pierwszego argumentu (`Short`) znajduje się w zakresie odpowiadającego mu parametru na typ (`Byte`). Następnie program eliminuje trzeci przeciążenia ponieważ każdy argument typu w drugim przeciążenia (`Short` i `Single`) rozszerzenie do danego typu w trzecim przeciążenia (`Integer` i `Single`). Drugi przeciążenia wymaga mniej rozszerzenia, dlatego kompilator używa go do wywołania.  
  
 W wywołaniu drugi kompilator nie może wyeliminować żadnego przeciążenia na podstawie zawężanie. Eliminuje trzeci przeciążenia z tego samego powodu jak pierwsze wywołanie, ponieważ mogą wywoływać przeciążenia drugi z mniej rozszerzanie typy argumentów. Jednak kompilator nie można rozpoznać między pierwszym i drugim przeciążeń. Każdy ma jeden typ parametru zdefiniowanego rozszerzająca do danego typu w innym (`Byte` do `Short`, ale `Single` do `Double`). Kompilator generuje w związku z tym błąd rozpoznawania przeciążenia.  
  
 **Poprawne podejście:** aby można było wywoływanie procedury przeciążenia bez niejednoznaczność, użyj [CType — funkcja](../../../../visual-basic/language-reference/functions/ctype-function.md) do dopasowania argumentu typy danych do typów parametrów. W poniższym przykładzie pokazano wywołanie `z` rozpoznawania który wymusza na drugi przeciążenia.  
  
 [!code-vb[VbVbcnProcedures#65](./codesnippet/VisualBasic/troubleshooting-procedures_8.vb)]  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>Przeciążenia rozdzielczość opcjonalne i ParamArray-argumenty  
 Jeśli dwa przeciążenia procedury identycznych podpisach z tą różnicą, że jest zadeklarowany jako ostatni parametr [opcjonalnie](../../../../visual-basic/language-reference/modifiers/optional.md) w jednym i [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) w innych, kompilator rozpoznaje wywołania tej procedury zgodnie z najlepsze dopasowanie. Aby uzyskać więcej informacji, zobacz [rozpoznawanie przeciążenia](./overload-resolution.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Sub, procedury](./sub-procedures.md)  
 [Procedury funkcji](./function-procedures.md)  
 [Procedury właściwości](./property-procedures.md)  
 [Procedury operatorów](./operator-procedures.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Przeciążanie procedury](./procedure-overloading.md)  
 [Zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md)  
 [Rozpoznanie przeciążenia](./overload-resolution.md)
