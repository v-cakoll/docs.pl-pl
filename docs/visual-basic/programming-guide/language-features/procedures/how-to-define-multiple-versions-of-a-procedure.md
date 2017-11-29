---
title: 'Porady: definiowanie wielu wersji procedury (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1abeaa6806252005dd3abfab3ff60bafa0c0cef1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a>Porady: definiowanie wielu wersji procedury (Visual Basic)
Procedurę można zdefiniować w różnych wersjach przez *przeładowanie* go przy użyciu takiej samej nazwie, ale inną listą parametrów dla każdej wersji. Przeciążanie służy do definiowania kilka wersji blisko związane procedury bez konieczności odróżnić je według nazwy.  
  
 Aby uzyskać więcej informacji, zobacz [przeciążanie procedury](./procedure-overloading.md).  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a>Aby zdefiniować wielu wersji procedury  
  
1.  Zapis `Sub` lub `Function` instrukcji deklaracji dla każdej wersji procedury, które chcesz zdefiniować. Użyj takiej samej nazwie procedury w każdej deklaracji.  
  
2.  Należy poprzedzić `Sub` lub `Function` — słowo kluczowe w każdej deklaracji z [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) — słowo kluczowe. Opcjonalnie można pominąć `Overloads` w deklaracjach, ale jeśli należy uwzględnić w deklaracji, należy go dołączyć w każdej deklaracji.  
  
3.  Po każdej instrukcji deklaracji napisać kod procedury obsługi konkretnego przypadku, gdy kod wywołujący dostarcza argumentów dopasowania listy parametrów w tej wersji. Nie masz do testowania dla parametrów, które dostarczył kodu wywołującego. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]formant przechodzi do tej samej wersji procedury.  
  
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
 [Procedury rozwiązywania problemów](./troubleshooting-procedures.md)  
 [Porady: przeciążanie procedury wykorzystującej parametry opcjonalne](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Porady: przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md)  
 [Rozpoznanie przeciążenia](./overload-resolution.md)
