---
title: End — Instrukcja
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
ms.openlocfilehash: cb2fb4abb21b7b9c6575cec4aca1374f63687607
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343723"
---
# <a name="end-statement"></a>End — Instrukcja
Kończy wykonywanie natychmiast.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
End  
```  
  
## <a name="remarks"></a>Uwagi  
 Instrukcję `End` można umieścić w dowolnym miejscu procedury, aby wymusić, że cała aplikacja przestanie działać. `End` zamyka wszystkie pliki otwierane za pomocą instrukcji `Open` i czyści wszystkie zmienne aplikacji. Aplikacja jest zamykana natychmiast, gdy nie ma żadnych innych programów przechowujących odwołania do jego obiektów i żaden z jego kodu nie jest uruchomiony.  
  
> [!NOTE]
> Instrukcja `End` uniemożliwia nieoczekiwane wykonanie kodu i nie wywołuje metody `Dispose` lub `Finalize` ani żadnego innego kodu Visual Basic. Odwołania do obiektów przechowywane przez inne programy są unieważnione. Jeśli w bloku `Try` lub `Catch` wystąpi instrukcja `End`, formant nie przejdzie do odpowiedniego bloku `Finally`.  
  
 Instrukcja `Stop` wstrzymuje wykonywanie, ale w przeciwieństwie do `End`, nie zamyka żadnych plików ani nie czyści żadnych zmiennych, chyba że zostanie napotkana w skompilowanym pliku wykonywalnym (. exe).  
  
 Ponieważ `End` kończy działanie aplikacji bez udziału w żadnym z zasobów, które mogą być otwarte, należy spróbować oczyścić się nieprzerwanie przed użyciem. Na przykład jeśli aplikacja ma otwarte jakiekolwiek formularze, należy je zamknąć przed przekroczeniem przez formant `End` instrukcji.  
  
 Należy używać `End` oszczędnie i tylko wtedy, gdy trzeba natychmiast zatrzymać. Normalne metody kończenia procedury (instrukcja[Return](../../../visual-basic/language-reference/statements/return-statement.md) i [Exit](../../../visual-basic/language-reference/statements/exit-statement.md)) nie tylko zamykają procedurę, ale również powodują, że kod wywołujący może czyścić się nieprzerwanie. Aplikacja konsolowa, na przykład, może po prostu `Return` z procedury `Main`.  
  
> [!IMPORTANT]
> Instrukcja `End` wywołuje metodę <xref:System.Environment.Exit%2A> klasy <xref:System.Environment> w przestrzeni nazw <xref:System>. <xref:System.Environment.Exit%2A> wymaga `UnmanagedCode` uprawnienia. Jeśli tego nie zrobisz, wystąpi błąd <xref:System.Security.SecurityException>.  
  
 Po wykonaniu dodatkowego słowa kluczowego [End \<słowo kluczowe > instrukcji](../../../visual-basic/language-reference/statements/end-keyword-statement.md) wyznacza końca definicji odpowiedniej procedury lub bloku. Na przykład `End Function` kończy definicję procedury `Function`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa instrukcji `End`, aby przerwać wykonywanie kodu, jeśli użytkownik zażąda.  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a>Uwagi dla deweloperów inteligentnych urządzeń  
 Ta instrukcja nie jest obsługiwana.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [Stop, instrukcja](../../../visual-basic/language-reference/statements/stop-statement.md)
- [End \<słowo kluczowe > instrukcji](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
