---
title: End — instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.End
- End
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- End keyword [Visual Basic], End statements
- programs [Visual Basic], quitting
- code, exiting
- program termination
- End statement [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
ms.openlocfilehash: a2c211e5ebfd00a639644243312cbe25f71f4cde
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54593709"
---
# <a name="end-statement"></a>End — Instrukcja
Kończy wykonywanie natychmiast.  
  
## <a name="syntax"></a>Składnia  
  
```  
End  
```  
  
## <a name="remarks"></a>Uwagi  
 Możesz umieścić `End` instrukcji procedury, aby wymusić całej aplikacji, aby zatrzymać w dowolnym miejscu. `End` Zamyka wszystkie pliki otwarte z `Open` instrukcji i czyści zmienne wszystkich aplikacji. Aplikacja zostanie zamknięta, nie są żadne inne programy, zawierający odwołania do obiektów, a nie działa żadna jego kodu.  
  
> [!NOTE]
>  `End` Instrukcji zatrzymuje wykonywanie kodu nagle i nie wywołuje `Dispose` lub `Finalize` metody i wszelki inny kod języka Visual Basic. Odwołania do obiektów przechowywanych przez inne programy nie są unieważniane. Jeśli `End` instrukcji występuje w ciągu `Try` lub `Catch` bloku, formant nie przekaże do odpowiednich `Finally` bloku.  
  
 Instrukcja `Stop` wstrzymuje wykonywanie, ale w przeciwieństwie do `End` nie zamyka żadnych plików ani nie czyści żadnych zmiennych — chyba że występuje w skompilowanym pliku wykonywalnym (.exe).  
  
 Ponieważ `End` kończy działanie aplikacji bez uczestniczenia do żadnych zasobów, które mogą być otwarte, należy starać się wstrzymuje prawidłowo, przed jego użyciem. Na przykład, jeśli aplikacja ma wszystkie formularze, Otwórz, należy zamknąć je przed kontrola osiąga `End` instrukcji.  
  
 Należy używać `End` oszczędnie i tylko wtedy kiedy należy zatrzymać natychmiast. Normalne sposobów, aby zakończyć procedurę ([instrukcji Return](../../../visual-basic/language-reference/statements/return-statement.md) i [instrukcji zakończenia](../../../visual-basic/language-reference/statements/exit-statement.md)) nie tylko zamknięcia w procedurze nie pozostawia żadnych śladów, ale również przyznać kod wywołujący możliwość wstrzymuje nie pozostawia żadnych śladów. Aplikację konsolową w języku, na przykład, można po prostu `Return` z `Main` procedury.  
  
> [!IMPORTANT]
>  `End` Instrukcja wywołuje <xref:System.Environment.Exit%2A> metody <xref:System.Environment> klasy w <xref:System> przestrzeni nazw. <xref:System.Environment.Exit%2A> Musisz mieć `UnmanagedCode` uprawnień. W takim przypadku, <xref:System.Security.SecurityException> wystąpi błąd.  
  
 Gdy następuje dodatkowego kluczowego [zakończenia \<— słowo kluczowe > instrukcji](../../../visual-basic/language-reference/statements/end-keyword-statement.md) wyznacza koniec definicji odpowiednią procedurę lub blok. Na przykład `End Function` kończy definicję `Function` procedury.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `End` instrukcję, aby zakończyć wykonywanie kodu, jeśli użytkownik żąda ona.  
  
 [!code-vb[VbVersHelp60Controls#64](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/end-statement_1.vb)]  
  
## <a name="smart-device-developer-notes"></a>Uwagi dla deweloperów urządzeń inteligentnych  
 Ta instrukcja nie jest obsługiwana.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [Stop, instrukcja](../../../visual-basic/language-reference/statements/stop-statement.md)
- [Koniec \<— słowo kluczowe > — instrukcja](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
