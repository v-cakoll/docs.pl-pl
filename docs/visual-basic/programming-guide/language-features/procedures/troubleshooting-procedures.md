---
title: Procedury rozwiązywania problemów (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting Visual Basic, procedures
- procedures [Visual Basic], troubleshooting
- Visual Basic code, procedures
- troubleshooting procedures
- procedures [Visual Basic], about procedures
ms.assetid: 525721e8-2e02-4f75-b5d8-6b893462cf2b
ms.openlocfilehash: 5ef0a485a0b114f465aac694970ec3350b26f35a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648550"
---
# <a name="troubleshooting-procedures-visual-basic"></a>Procedury rozwiązywania problemów (Visual Basic)
Ta strona zawiera listę typowych problemów występujących podczas pracy z procedurami.  
  
## <a name="returning-an-array-type-from-a-function-procedure"></a>Zwraca typ tablicy z procedury — funkcja  
 Jeśli `Function` procedury zwraca typ danych tablicy, nie można użyć `Function` nazwy do przechowywania wartości elementów w tablicy. Jeśli użytkownik spróbuje to zrobić, kompilator zinterpretuje ją jako wywołanie `Function`. Poniższy przykład generuje błędy kompilatora.  
  
 `Function allOnes(ByVal n As Integer) As Integer()`  
  
 `For i As Integer = 1 To n - 1`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `allOnes(i) = 1`  
  
 `Next i`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `Return allOnes()`  
  
 `End Function`  
  
 Wykonywanie instrukcji `allOnes(i) = 1` generuje błąd kompilatora, ponieważ może on wywołać `allOnes` z nieprawidłowym argumentem niewłaściwy typ danych (pojedynczego `Integer` zamiast `Integer` tablicy). Wykonywanie instrukcji `Return allOnes()` generuje błąd kompilatora, ponieważ może on wywołać `allOnes` z żadnego argumentu.  
  
 **Właściwe podejście:** Aby móc modyfikować elementy w tablicy, która jest zwracana, należy zdefiniować tablicę wewnętrzny jako zmienna lokalna. Poniższy przykład skompiluje się bez błędów.  
  
 [!code-vb[VbVbcnProcedures#66](./codesnippet/VisualBasic/troubleshooting-procedures_1.vb)]  
  
## <a name="argument-not-being-modified-by-procedure-call"></a>Argument nie jest modyfikowany przez wywołanie procedury  
 Jeśli zamierzasz zezwolić procedury można zmienić elementu programistycznego, bazowy argumentu w wywoływanym kodzie, musisz przekazać go przez odwołanie. Ale procedury mogą uzyskać dostęp do elementów argumentu typu odwołania, nawet wtedy, gdy przekazywane przez wartość.  
  
-   **Bazowy zmiennej**. Aby zezwolić na procedury zastąpić wartość zmiennej bazowego samego elementu, procedury należy zadeklarować parametr [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md). Ponadto kod wywołujący nie ująć argument w nawiasach, ponieważ mogłoby, które zastępują `ByRef` mechanizm przekazywania.  
  
-   **Elementy typu odwołania**. Przy deklarowaniu parametru [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md), procedury nie można zmodyfikować bazowego zmiennej elementu. Jednak jeśli argument jest typem referencyjnym, procedura modyfikować elementów członkowskich obiektu, na który wskazuje, nawet jeśli nie można zastąpić, wartość zmiennej. Na przykład jeśli argument jest zmienną tablicową, procedury nie można przypisać nową tablicę do niego, ale można zmienić, co najmniej jeden z jego elementów. Zmienione elementy są odzwierciedlane w podstawowej zmienną tablicy w wywoływanym kodzie.  
  
 W poniższym przykładzie zdefiniowano dwie procedury potrwać zmienną tablicową według wartości, które działają na jego elementach. Procedura `increase` po prostu dodaje je do każdego elementu. Procedura `replace` przypisuje nową tablicę z parametrem `a()` , a następnie dodaje je do każdego elementu. Jednak ponowne przypisanie nie ma wpływu na podstawowe zmienną tablicy w wywoływanym kodzie ponieważ `a()` zadeklarowano `ByVal`.  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/troubleshooting-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/troubleshooting-procedures_3.vb)]  
  
 Poniższy przykład wykonuje wywołania `increase` i `replace`.  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/troubleshooting-procedures_4.vb)]  
  
 Pierwszy `MsgBox` wywołać Wyświetla "po increase(n): 11, 21, 31, 41". Ponieważ `n` jest typem referencyjnym `increase` można zmienić jej członków, nawet jeśli jest przekazywana `ByVal`.  
  
 Drugi `MsgBox` wywołać Wyświetla "po replace(n): 11, 21, 31, 41". Ponieważ `n` jest przekazywany `ByVal`, `replace` nie można zmodyfikować zmienną `n` przez przypisanie nowej tablicy. Gdy `replace` tworzy nowe wystąpienie tablicy `k` i przypisuje go do zmiennej lokalnej `a`, utracie odwołanie do `n` przekazany kod wywołujący. Gdy zwiększa członkowie `a`, tylko lokalnej tablicy `k` dotyczy problem.  
  
 **Właściwe podejście:** Aby można było zmodyfikować samego podstawowego elementu zmiennej, przekazać go przez odwołanie. Poniższy kod przedstawia zmiany w deklaracji `replace` która umożliwia zastąpienie jednej tablicy na inną w wywoływanym kodzie.  
  
 [!code-vb[VbVbcnProcedures#64](./codesnippet/VisualBasic/troubleshooting-procedures_5.vb)]  
  
## <a name="unable-to-define-an-overload"></a>Nie można zdefiniować przeciążenia  
 Jeśli chcesz zdefiniować przeciążoną wersję procedurę, musisz podać samą nazwę, ale inny podpis. Jeśli kompilator nie można odróżnić swojej deklaracji z przeciążenia z tym samym podpisie, spowoduje wygenerowanie błędu.  
  
 *Podpisu* procedura zależy od nazwy procedury i listy parametrów. Każde przeciążenie musi mieć taką samą nazwę jak wszystkie inne przeciążenia, ale muszą różnić się od wszystkich z nich w co najmniej jeden ze składników podpisu. Aby uzyskać więcej informacji, zobacz [przeciążanie procedury](./procedure-overloading.md).  
  
 Następujące elementy, mimo że odnoszą się do listy parametrów nie są składniki sygnatury procedury:  
  
-   Słowa kluczowe modyfikator procedury, takich jak `Public`, `Shared`, i `Static`  
  
-   Nazwy parametrów  
  
-   Słowa kluczowe modyfikator parametrów, takich jak `ByRef` i `Optional`  
  
-   Typ danych wartości zwracanej (z wyjątkiem operatora konwersji)  
  
 Procedury nie mogą przeciążać przez zróżnicowanie tylko co najmniej jeden z wymienionych elementów.  
  
 **Właściwe podejście:** Aby można było zdefiniować przeciążenia procedurę, trzeba zmieniać podpis. Musisz użyć takiej samej nazwie, gdy trzeba zmieniać liczbę, kolejność lub typów danych parametrów. Ogólna procedura może się różnić liczbę parametrów typu. W operator konwersji ([funkcja CType](../../../../visual-basic/language-reference/functions/ctype-function.md)), zwracany typ może się różnić.  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>Przeciążenia rozdzielczość z opcjonalnymi i ParamArray-argumenty  
 Jeśli są przeciążanie procedury z jednej lub kilku [opcjonalne](../../../../visual-basic/language-reference/modifiers/optional.md) parametrów lub [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametru, użytkownik musi uniknąć duplikowania wszystkich *niejawne przeładowania*. Aby uzyskać informacje, zobacz [zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md).  
  
## <a name="calling-a-wrong-version-of-an-overloaded-procedure"></a>Wywoływanie niewłaściwą wersję procedury przeciążenia  
 Jeśli procedura ma kilka przeciążone wersje, należy należy zapoznać się z ich list parametrów i zrozumieć, jak Visual Basic jest rozpoznawana jako wywołania między przeciążenia. W przeciwnym razie można wywoływać przeciążenia innym niż zamierzony.  
  
 Po określeniu przeciążenia, które ma zostać wywołana Uważaj obserwować następujące reguły:  
  
-   Podaj prawidłową liczbę argumentów i w odpowiedniej kolejności.  
  
-   W idealnym przypadku argumenty powinny mieć dokładnie te same typy danych jako odpowiednich parametrów. W każdym przypadku typ danych każdego argumentu musi mogą zostać poszerzone do, jego odpowiadającego mu parametru. Ta zasada obowiązuje nawet w przypadku [Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md) równa `Off`. Jeśli przeciążenia wymaga wszelkie konwersja zawężająca z listy argumentów, które przeciążenia nie jest uprawnione do wywołania.  
  
-   Jeśli podasz argumenty, które wymagają rozszerzenia, należy ich typów danych, jak najbliżej odpowiednich typów danych parametrów. Jeśli dwa lub więcej przeciążenia akceptuje argument typów danych, kompilator rozpoznaje wywołania do przeciążenia, które wymaga minimalnej liczbie rozszerzanie.  
  
 Można zmniejszyć ryzyko niezgodności typu danych przy użyciu [funkcja CType](../../../../visual-basic/language-reference/functions/ctype-function.md) konwersji — słowo kluczowe podczas przygotowywania argumenty.  
  
### <a name="overload-resolution-failure"></a>Błąd rozpoznawania przeciążenia  
 Po wywołaniu procedury przeciążenia, kompilator spróbuje wyeliminować wszystkie oprócz jednego z przeciążeń. Jeśli się powiedzie, jest rozpoznawana jako wywołanie tego przeciążenia. Jeśli eliminuje wszystkie przeciążenia lub nie można zmniejszyć, przeciążenia kwalifikujących się do pojedynczego Release candidate, spowoduje wygenerowanie błędu.  
  
 Poniższy przykład ilustruje procesu rozpoznawania przeciążenia.  
  
 [!code-vb[VbVbcnProcedures#62](./codesnippet/VisualBasic/troubleshooting-procedures_6.vb)]  
  
 [!code-vb[VbVbcnProcedures#63](./codesnippet/VisualBasic/troubleshooting-procedures_7.vb)]  
  
 W pierwszym wywołaniu kompilator eliminuje pierwsze przeciążenie, ponieważ typ pierwszego argumentu (`Short`) powoduje zawężenie typu odpowiadającego mu parametru (`Byte`). Następnie eliminuje trzecie przeciążenie ponieważ każdy argument typu w drugie przeciążenie (`Short` i `Single`) rozszerza się na odpowiedni typ w trzecie przeciążenie (`Integer` i `Single`). Drugie przeciążenie wymaga mniej rozszerzenia, dlatego kompilator używa go na potrzeby wywołania.  
  
 W drugim wywołaniu kompilator nie może wyeliminować żadnego przeciążenia na podstawie zawężanie. Eliminuje to trzecie przeciążenie dla tego samego powodu, tak jak w pierwszym wywołaniu, ponieważ może wywołać drugie przeciążenie z mniej rozszerzanie typy argumentów. Jednak kompilator nie może rozpoznać między przeciążeniami pierwszego i drugiego. Każda z nich ma jeden typ zdefiniowany parametr, który rozszerza się na odpowiedni typ w innym (`Byte` do `Short`, ale `Single` do `Double`). Kompilator generuje w związku z tym błędem rozpoznawania przeciążenia.  
  
 **Właściwe podejście:** Aby umożliwić wywoływanie procedury przeciążenia bez niejasności, należy użyć [funkcja CType](../../../../visual-basic/language-reference/functions/ctype-function.md) do dopasowania typy danych argumentów do typów parametrów. W poniższym przykładzie pokazano wywołanie `z` rozdzielczości, wymusza na drugie przeciążenie.  
  
 [!code-vb[VbVbcnProcedures#65](./codesnippet/VisualBasic/troubleshooting-procedures_8.vb)]  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>Przeciążenia rozdzielczość z opcjonalnymi i ParamArray-argumenty  
 Jeśli dwa przeciążenia procedury, posiadające identyczne oznaczenie, z tą różnicą, że ostatni parametr jest zadeklarowana [opcjonalnie](../../../../visual-basic/language-reference/modifiers/optional.md) w jednym i [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) w innych, kompilator rozpoznaje wywołania tej procedury zgodnie z najlepiej dopasowany. Aby uzyskać więcej informacji, zobacz [rozdzielczość przeciążenia](./overload-resolution.md).  
  
## <a name="see-also"></a>Zobacz także
- [Procedury](./index.md)
- [Sub, procedury](./sub-procedures.md)
- [Procedury funkcji](./function-procedures.md)
- [Procedury właściwości](./property-procedures.md)
- [Procedury operatorów](./operator-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Przeciążanie procedury](./procedure-overloading.md)
- [Zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md)
- [Rozpoznanie przeciążenia](./overload-resolution.md)
