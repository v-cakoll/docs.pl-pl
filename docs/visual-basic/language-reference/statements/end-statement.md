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
ms.openlocfilehash: 9307cf10e6125441bd49baa0e663a5a13f234005
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944464"
---
# <a name="end-statement"></a>End — Instrukcja
Kończy wykonywanie natychmiast.  
  
## <a name="syntax"></a>Składnia  
  
```  
End  
```  
  
## <a name="remarks"></a>Uwagi  
 Możesz umieścić `End` instrukcję w dowolnym miejscu procedury, aby wymusić, że cała aplikacja przestanie działać. `End`zamyka wszystkie pliki otwierane za `Open` pomocą instrukcji i czyści wszystkie zmienne aplikacji. Aplikacja jest zamykana natychmiast, gdy nie ma żadnych innych programów przechowujących odwołania do jego obiektów i żaden z jego kodu nie jest uruchomiony.  
  
> [!NOTE]
> Instrukcja kończy wykonywanie kodu nieoczekiwanie i nie `Dispose` wywołuje metody lub `Finalize` ani żadnego innego kodu Visual Basic. `End` Odwołania do obiektów przechowywane przez inne programy są unieważnione. Jeśli instrukcja jest napotkana `Try` w bloku lub `Catch` , formant nie przechodzi do odpowiadającego `Finally` bloku. `End`  
  
 Instrukcja `Stop` wstrzymuje wykonywanie, ale w przeciwieństwie do `End` nie zamyka żadnych plików ani nie czyści żadnych zmiennych — chyba że występuje w skompilowanym pliku wykonywalnym (.exe).  
  
 Ponieważ `End` kończy działanie aplikacji bez udziału w zasobach, które mogą być otwarte, należy spróbować oczyścić się nieprzerwanie przed użyciem. Na przykład jeśli aplikacja ma otwarte jakiekolwiek formularze, należy je zamknąć przed przekroczeniem przez `End` formant.  
  
 Należy używać `End` oszczędnie i tylko wtedy, gdy trzeba natychmiast zatrzymać. Normalne metody kończenia procedury (instrukcja[Return](../../../visual-basic/language-reference/statements/return-statement.md) i [Exit](../../../visual-basic/language-reference/statements/exit-statement.md)) nie tylko zamykają procedurę, ale również powodują, że kod wywołujący może czyścić się nieprzerwanie. Aplikacja konsolowa, na przykład, może po `Return` prostu `Main` wykonać procedurę.  
  
> [!IMPORTANT]
> `End` Instrukcja<xref:System.Environment.Exit%2A> wywołuje metodę<xref:System.Environment> klasy w<xref:System> przestrzeni nazw. <xref:System.Environment.Exit%2A>`UnmanagedCode` wymaga uprawnienia. Jeśli tego nie zrobisz, <xref:System.Security.SecurityException> wystąpi błąd.  
  
 Po wykonaniu dodatkowego słowa kluczowego [End \<słowo kluczowe > instrukcja](../../../visual-basic/language-reference/statements/end-keyword-statement.md) wyznacza końca definicji odpowiedniej procedury lub bloku. Na przykład `End Function` kończy definicję `Function` procedury.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa instrukcji, `End` aby przerwać wykonywanie kodu, jeśli użytkownik zażąda.  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a>Uwagi dla deweloperów urządzeń inteligentnych  
 Ta instrukcja nie jest obsługiwana.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [Stop, instrukcja](../../../visual-basic/language-reference/statements/stop-statement.md)
- [End \<słowo kluczowe > instrukcji](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
