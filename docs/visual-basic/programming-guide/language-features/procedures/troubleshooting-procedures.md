---
title: Procedury rozwiązywania problemów
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting Visual Basic, procedures
- procedures [Visual Basic], troubleshooting
- Visual Basic code, procedures
- troubleshooting procedures
- procedures [Visual Basic], about procedures
ms.assetid: 525721e8-2e02-4f75-b5d8-6b893462cf2b
ms.openlocfilehash: 8d4c4929e299efb12d283492a101c18ae794110b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352514"
---
# <a name="troubleshooting-procedures-visual-basic"></a>Procedury rozwiązywania problemów (Visual Basic)

Ta strona zawiera listę typowych problemów, które mogą wystąpić podczas pracy z procedurami.  
  
## <a name="returning-an-array-type-from-a-function-procedure"></a>Zwracanie typu tablicy z procedury funkcji

Jeśli `Function` procedura zwraca typ danych tablicy, nie można użyć nazwy `Function` do przechowywania wartości w elementach tablicy. Jeśli podjęto próbę wykonania tej czynności, kompilator interpretuje ją jako wywołanie do `Function`. Poniższy przykład generuje błędy kompilatora:
  
```vb
Function AllOnes(n As Integer) As Integer()
   For i As Integer = 1 To n - 1  
      ' The following statement generates a COMPILER ERROR.  
      AllOnes(i) = 1  
   Next  

   ' The following statement generates a COMPILER ERROR.  
   Return AllOnes()  
End Function
```

Instrukcja `AllOnes(i) = 1` generuje błąd kompilatora, ponieważ wydaje się, że wywołuje `AllOnes` z argumentem niewłaściwego typu danych (`Integer` skalarną zamiast tablicy `Integer`). Instrukcja `Return AllOnes()` generuje błąd kompilatora, ponieważ wydaje się, że wywoływany `AllOnes` bez argumentu.  
  
 **Poprawne podejście:** Aby można było modyfikować elementy tablicy, która ma zostać zwrócona, zdefiniuj tablicę wewnętrzną jako zmienną lokalną. Poniższy przykład kompiluje się bez błędu:

 [!code-vb[VbVbcnProcedures#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#66)]

## <a name="argument-not-modified-by-procedure-call"></a>Argument nie został zmodyfikowany przez wywołanie procedury

Jeśli zamierzasz zezwolić procedurze na zmianę elementu programistycznego bazowego argumentu w wywoływanym kodzie, musisz przekazać go przez odwołanie. Ale procedura może uzyskać dostęp do elementów argumentu typu odwołania, nawet jeśli przekażesz go przez wartość.

- **Zmienna bazowa**. Aby zezwolić procedurze na zastępowanie wartości bazowego elementu zmiennej, procedura musi deklarować parametr [ByRef](../../../language-reference/modifiers/byref.md). Ponadto kod wywołujący nie może ujmować argumentu w nawiasach, ponieważ spowodowałoby to przesłonięcie `ByRef` mechanizmu przekazywania.

- **Elementy typu referencyjnego**. Jeśli deklarujesz parametr [ByVal](../../../language-reference/modifiers/byval.md), procedura nie może zmodyfikować bazowego elementu zmiennej. Jeśli jednak argument jest typem referencyjnym, procedura może modyfikować elementy członkowskie obiektu, do którego wskazuje, nawet jeśli nie może zastąpić wartości zmiennej. Na przykład, jeśli argument jest zmienną tablicową, procedura nie może przypisać do niej nowej tablicy, ale może zmienić jeden lub więcej elementów. Zmienione elementy są odzwierciedlone w źródłowej zmiennej tablicowej w kodzie wywołującym.

W poniższym przykładzie zdefiniowano dwie procedury, które pobierają zmienną tablicową według wartości i działają na jej elementach. Procedura `increase` po prostu dodaje jeden do każdego elementu. Procedura `replace` przypisuje nową tablicę do parametru `a()` a następnie dodaje ją do każdego elementu. Jednak ponowne przypisanie nie ma wpływu na podstawową zmienną tablicową w kodzie wywołującym, ponieważ `a()` jest zadeklarowana `ByVal`.

[!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]

[!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]

Poniższy przykład wykonuje wywołania `increase` i `replace`:

[!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]
  
Pierwsze wywołanie `MsgBox` wyświetla "po zwiększeniu (n): 11, 21, 31, 41". Ponieważ `n` jest typem referencyjnym, `increase` może zmienić jego składowe, nawet jeśli zostanie on przesłany `ByVal`.

Drugie wywołanie `MsgBox` wyświetla "po zastąpieniu (n): 11, 21, 31, 41". Ponieważ `n` jest przenoszona `ByVal`, `replace` nie może zmodyfikować zmiennej `n` przez przypisanie do niej nowej tablicy. Gdy `replace` tworzy nowe wystąpienie tablicy `k` i przypisze je do zmiennej lokalnej `a`, utraci odwołanie do `n` przekazaną przez kod wywołujący. Po zwiększeniu liczby elementów członkowskich `a`dotyczy tylko `k` tablicy lokalnej.

**Poprawne podejście:** Aby można było zmodyfikować bazowy element zmiennej, przekaż go przez odwołanie. Poniższy przykład pokazuje zmianę w deklaracji `replace`, która umożliwia jej zastąpienie jednej tablicy innym w kodzie wywołującym:

[!code-vb[VbVbcnProcedures#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#64)]

## <a name="unable-to-define-an-overload"></a>Nie można zdefiniować przeciążenia

Jeśli chcesz zdefiniować przeciążoną wersję procedury, należy użyć tej samej nazwy, ale innej sygnatury. Jeśli kompilator nie może odróżnić deklaracji od przeciążenia z tym samym podpisem, generuje błąd.

*Podpis* procedury jest określany na podstawie nazwy procedury i listy parametrów. Każde Przeciążenie musi mieć taką samą nazwę jak wszystkie inne przeciążenia, ale muszą się różnić od wszystkich w co najmniej jednym z pozostałych składników podpisu. Aby uzyskać więcej informacji, zobacz [przeciążanie procedur](./procedure-overloading.md).

Następujące elementy, chociaż odnoszą się do listy parametrów, nie są częścią podpisu procedury:

- Słowa kluczowe modyfikujące procedurę, takie jak `Public`, `Shared`i `Static`.
- Nazwy parametrów.
- Słowa kluczowe modyfikatora parametru, takie jak `ByRef` i `Optional`.
- Typ danych wartości zwracanej (z wyjątkiem operatora konwersji).

Nie można przeciążyć procedury, zmieniając tylko jeden lub więcej z poprzednich elementów.

**Poprawne podejście:** Aby można było zdefiniować Przeciążenie procedury, należy zmienić sygnaturę. Ponieważ należy użyć tej samej nazwy, należy zmienić liczbę, kolejność lub typy danych parametrów. W procedurze ogólnej można zmienić liczbę parametrów typu. W operatorze konwersji ([Funkcja CType](../../../language-reference/functions/ctype-function.md)) można zróżnicować typ zwracany.

### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>Rozpoznawanie przeciążenia przy użyciu argumentów opcjonalnych i ParamArray

Jeśli przeładujesz procedurę z co najmniej jednym parametrem [opcjonalnym](../../../language-reference/modifiers/optional.md) lub parametrem [ParamArray](../../../language-reference/modifiers/paramarray.md) , musisz uniknąć duplikowania dowolnego *niejawnego przeciążenia*. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md).

## <a name="calling-the-wrong-version-of-an-overloaded-procedure"></a>Wywoływanie niewłaściwej wersji przeciążonej procedury

Jeśli procedura zawiera kilka przeciążonych wersji, należy zapoznać się ze wszystkimi ich listami parametrów i zrozumieć, jak Visual Basic rozpoznaje wywołania między przeciążeniami. W przeciwnym razie można wywołać Przeciążenie inne niż zamierzone.

Po ustaleniu, którego przeciążenia chcesz wywołać, należy uważnie przestrzegać następujących zasad:

- Podaj poprawną liczbę argumentów, a w odpowiedniej kolejności.  
- W idealnym przypadku argumenty powinny mieć dokładnie te same typy danych co odpowiednie parametry. W każdym przypadku typ danych każdego argumentu musi być rozszerzony do odpowiadającego mu parametru. Jest to prawdziwe nawet z [opcją Strict Option](../../../language-reference/statements/option-strict-statement.md) ustawioną na `Off`. Jeśli Przeciążenie wymaga wszelkiej konwersji zawężanej z listy argumentów, Przeciążenie nie jest uprawnione do wywoływania.
- W przypadku podania argumentów, które wymagają poszerzenia, należy sprawić, aby ich typy danych były zbliżone jak najprawdopodobniej do odpowiednich typów danych parametrów. Jeśli co najmniej dwa przeciążenia akceptują typy danych argumentów, kompilator rozpoznaje wywołanie przeciążenia, które wywołuje najmniejszą ilość rozszerzania.

Podczas przygotowywania argumentów można zmniejszyć prawdopodobieństwo niezgodności typów danych przy użyciu słowa kluczowego konwersji [funkcji CType](../../../language-reference/functions/ctype-function.md) .

### <a name="overload-resolution-failure"></a>Niepowodzenie rozpoznawania przeciążenia

Gdy wywołujesz przeciążoną procedurę, kompilator próbuje wyeliminować wszystkie oprócz jednego z przeciążeń. Jeśli to się powiedzie, rozwiązuje wywołanie do tego przeciążenia. Jeśli eliminuje wszystkie przeciążenia lub nie może zmniejszyć kwalifikujących się przeciążeń do pojedynczego kandydata, generuje błąd.

Poniższy przykład ilustruje proces rozwiązywania przeciążenia:

[!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]

[!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]
  
W pierwszym wywołaniu kompilator eliminuje pierwsze Przeciążenie, ponieważ typ pierwszego argumentu (`Short`) jest wąski do typu odpowiadającego mu parametru (`Byte`). Następnie eliminuje trzecie Przeciążenie, ponieważ każdy typ argumentu w drugim przeciążeniu (`Short` i `Single`) poszerza do odpowiedniego typu w trzecim przeciążenia (`Integer` i `Single`). Drugie Przeciążenie wymaga mniej poszerzania, więc kompilator używa go do wywołania.

W drugim wywołaniu kompilator nie może wyeliminować żadnych przeciążeń na podstawie zawężania. Eliminuje trzecie Przeciążenie z tego samego powodu, co w pierwszym wywołaniu, ponieważ może wywoływać drugie Przeciążenie przy mniejszej poszerzeniu typów argumentów. Jednak kompilator nie może rozpoznać pierwszego i drugiego przeciążenia. Każdy z nich ma jeden zdefiniowany typ parametru, który jest poszerzany do odpowiedniego typu w drugim (`Byte` do `Short`, ale `Single` do `Double`). W związku z tym kompilator generuje błąd rozpoznawania przeciążenia.

**Poprawne podejście:** Aby można było wywołać przeciążoną procedurę bez niejednoznaczności, należy użyć [funkcji CType](../../../language-reference/functions/ctype-function.md) do dopasowania typów danych argumentów do typów parametrów. W poniższym przykładzie pokazano wywołanie `z`, które wymusza rozdzielczość do drugiego przeciążenia.

[!code-vb[VbVbcnProcedures#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#65)]

### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>Rozpoznawanie przeciążenia przy użyciu argumentów opcjonalnych i ParamArray

Jeśli dwa przeciążenia procedury mają identyczne podpisy, z wyjątkiem tego, że ostatni parametr jest zadeklarowany jako [opcjonalny](../../../language-reference/modifiers/optional.md) w jednym i [ParamArray](../../../language-reference/modifiers/paramarray.md) w drugim, kompilator rozpoznaje wywołanie tej procedury zgodnie z najbliższym dopasowaniem. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie przeciążenia](./overload-resolution.md).

## <a name="see-also"></a>Zobacz także

- [Procedury](index.md)
- [Sub, procedury](sub-procedures.md)
- [Procedury funkcji](function-procedures.md)
- [Procedury właściwości](property-procedures.md)
- [Procedury operatorów](operator-procedures.md)
- [Parametry i argumenty procedur](procedure-parameters-and-arguments.md)
- [Przeciążanie procedury](procedure-overloading.md)
- [Zagadnienia dotyczące przeciążania procedur](considerations-in-overloading-procedures.md)
- [Rozpoznanie przeciążenia](overload-resolution.md)
