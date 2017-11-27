---
title: "Porady: przeciążanie procedury wykorzystującej parametry opcjonalne (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b4a863944d4f9ab265aab52578fbb704ca376de5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a>Porady: przeciążanie procedury wykorzystującej parametry opcjonalne (Visual Basic)
Jeśli procedura ma co najmniej jeden [opcjonalnie](../../../../visual-basic/language-reference/modifiers/optional.md) parametrów, nie można zdefiniować przeciążonego wersji zgodne z żadnym z jego niejawne przeładowania. Aby uzyskać więcej informacji, zobacz "Niejawne Overloads dla parametrów" w [zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md).  
  
## <a name="one-optional-parameter"></a>Jeden opcjonalny parametr  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a>Do procedury, która przyjmuje jeden parametr opcjonalny przeciążenia  
  
1.  Zapis `Sub` lub `Function` instrukcji deklaracji, która zawiera parametr opcjonalny na liście parametrów. Nie używaj `Optional` — słowo kluczowe w tej wersji przeciążona.  
  
2.  Należy poprzedzić `Sub` lub `Function` — słowo kluczowe z [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) — słowo kluczowe.  
  
3.  Pisanie kodu procedury, który powinien zostać wykonany, gdy kod wywołujący dostarcza opcjonalny argument.  
  
4.  Zakończenie procedury z `End Sub` lub `End Function` oświadczenie zależnie od potrzeb.  
  
5.  Zapis drugi instrukcji deklaracji, która jest taka sama jak pierwszej deklaracji z tą różnicą, że nie ma parametr opcjonalny na liście parametrów.  
  
6.  Pisanie kodu procedury, który powinien zostać wykonany, gdy kod wywołujący nie dostarcza opcjonalny argument. Zakończenie procedury z `End Sub` lub `End Function` oświadczenie zależnie od potrzeb.  
  
     W poniższym przykładzie przedstawiono procedurę zdefiniowane za pomocą opcjonalnego parametru równoważne zbiór dwie procedury przeciążenia, a na końcu przykłady zarówno nieprawidłowy prawidłowy zastąpionej wersji i.  
  
     [!code-vb[VbVbcnProcedures#59](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_2.vb)]  
  
     [!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_3.vb)]  
  
## <a name="multiple-optional-parameters"></a>Wiele następujące parametry opcjonalne  
 Procedury z więcej niż jeden parametr opcjonalny potrzebne są zwykle więcej niż dwie wersje przeciążona. Na przykład jeśli istnieją dwie opcjonalne parametry i kod wywołujący może dostarczyć lub Pomiń nich niezależnie od innych, należy cztery przeciążone wersji narzędzia, dla każdej możliwej kombinacji podanych argumentów.  
  
 Jak zwiększa liczbę następujące parametry opcjonalne, zwiększa złożoności logowania. Chyba, że niektóre kombinacje podanych argumentów nie są dozwolone, N następujące parametry opcjonalne mają być 2 ^ N przeciążony wersji. W zależności od charakteru procedura może się okazać, że jasności logiki uzasadnia dodatkowy wysiłek zdefiniowania zastąpionej wersji.  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a>Aby przeciążanie procedury wykorzystującej więcej niż jeden parametr opcjonalny  
  
1.  Określ kombinacje podane argumenty opcjonalne są akceptowane przez logikę procedury. Kombinację niedopuszczalne mogą wystąpić, jeśli jeden parametr opcjonalny jest zależna od innej. Na przykład jeden parametr akceptuje współmałżonka nazwę i inny akceptuje współmałżonka wieku, kombinacja argumentów dostarczanie wiek, ale bez określenia nazwy jest nie do przyjęcia.  
  
2.  Dla każdej kombinacji dopuszczalne podanych argumentów opcjonalnych zapisu `Sub` lub `Function` instrukcji deklaracji, który definiuje na odpowiedniej liście parametrów. Nie używaj `Optional` — słowo kluczowe.  
  
3.  W każdej deklaracji poprzedzać `Sub` lub `Function` — słowo kluczowe z [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) — słowo kluczowe.  
  
4.  Po każdej deklaracji pisania kodu procedury, który powinien zostać wykonany po kod wywołujący dostarcza odpowiadającego tej deklaracji listy parametrów listy argumentów.  
  
5.  Zakończenie każdej procedury z `End Sub` lub `End Function` oświadczenie zależnie od potrzeb.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Parametry opcjonalne](./optional-parameters.md)  
 [Tablice parametrów](./parameter-arrays.md)  
 [Przeciążanie procedury](./procedure-overloading.md)  
 [Procedury rozwiązywania problemów](./troubleshooting-procedures.md)  
 [Porady: Definiowanie wielu wersji procedury](./how-to-define-multiple-versions-of-a-procedure.md)  
 [Porady: wywoływanie procedury przeciążenia](./how-to-call-an-overloaded-procedure.md)  
 [Porady: przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Rozpoznanie przeciążenia](./overload-resolution.md)
