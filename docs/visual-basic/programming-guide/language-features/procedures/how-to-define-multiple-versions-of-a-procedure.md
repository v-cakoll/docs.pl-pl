---
title: 'Porady: definiowanie wielu wersji procedury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: a4d0c5bbb07dd5433ff62179fc10a6274bf19364
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a>Porady: definiowanie wielu wersji procedury (Visual Basic)
Procedurę można zdefiniować w różnych wersjach przez *przeładowanie* go przy użyciu takiej samej nazwie, ale inną listą parametrów dla każdej wersji. Przeciążanie służy do definiowania kilka wersji blisko związane procedury bez konieczności odróżnić je według nazwy.  
  
 Aby uzyskać więcej informacji, zobacz [przeciążanie procedury](./procedure-overloading.md).  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a>Aby zdefiniować wielu wersji procedury  
  
1.  Zapis `Sub` lub `Function` instrukcji deklaracji dla każdej wersji procedury, które chcesz zdefiniować. Użyj takiej samej nazwie procedury w każdej deklaracji.  
  
2.  Należy poprzedzić `Sub` lub `Function` — słowo kluczowe w każdej deklaracji z [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) — słowo kluczowe. Opcjonalnie można pominąć `Overloads` w deklaracjach, ale jeśli należy uwzględnić w deklaracji, należy go dołączyć w każdej deklaracji.  
  
3.  Po każdej instrukcji deklaracji napisać kod procedury obsługi konkretnego przypadku, gdy kod wywołujący dostarcza argumentów dopasowania listy parametrów w tej wersji. Nie masz do testowania dla parametrów, które dostarczył kodu wywołującego. Visual Basic przejmuje kontrolę zgodną wersję procedury.  
  
4.  Zakończenie każdej wersji procedury z `End Sub` lub `End Function` oświadczenie zależnie od potrzeb.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano `Sub` procedury można opublikować transakcji bilans klienta. Używa `Overloads` — słowo kluczowe, aby zdefiniować dwie wersje procedury, jeden akceptujący klienta wg nazwy oraz innych według konta.  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/how-to-define-multiple-versions-of-a-procedure_1.vb)]  
  
 Kod wywołujący można uzyskać identyfikator klienta jako `String` lub `Integer`, a następnie użyć tej samej instrukcji wywoływania w każdym przypadku.  
  
 Aby uzyskać informacje dotyczące wywołania te wersje programu `post` procedury, zobacz [porady: wywoływanie procedury przeciążony](./how-to-call-an-overloaded-procedure.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Upewnij się, że każdy sieci przeciążona wersji ma taką samą nazwę procedury, ale inną listą parametrów.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Rozwiązywanie problemów z procedurami](./troubleshooting-procedures.md)  
 [Instrukcje: przeciążanie procedury korzystającej z parametrów opcjonalnych](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Instrukcje: przeciążanie procedury korzystającej z nieokreślonej liczby parametrów](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md)  
 [Rozpoznanie przeciążenia](./overload-resolution.md)
