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
ms.openlocfilehash: fe17a82662c4014069c77f2da76723a051ab9084
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404709"
---
# <a name="end-statement"></a>End — Instrukcja
Kończy wykonywanie natychmiast.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
End  
```  
  
## <a name="remarks"></a>Uwagi  
 Możesz umieścić `End` instrukcję w dowolnym miejscu procedury, aby wymusić, że cała aplikacja przestanie działać. `End`zamyka wszystkie pliki otwierane za pomocą `Open` instrukcji i czyści wszystkie zmienne aplikacji. Aplikacja jest zamykana natychmiast, gdy nie ma żadnych innych programów przechowujących odwołania do jego obiektów i żaden z jego kodu nie jest uruchomiony.  
  
> [!NOTE]
> `End`Instrukcja kończy wykonywanie kodu nieoczekiwanie i nie wywołuje `Dispose` `Finalize` metody lub ani żadnego innego kodu Visual Basic. Odwołania do obiektów przechowywane przez inne programy są unieważnione. Jeśli `End` instrukcja jest napotkana w `Try` bloku lub `Catch` , formant nie przechodzi do odpowiadającego `Finally` bloku.  
  
 `Stop`Instrukcja zawiesza wykonywanie, ale w przeciwieństwie do `End` siebie nie zamyka żadnych plików ani nie czyści żadnych zmiennych, chyba że występuje w skompilowanym pliku wykonywalnym (. exe).  
  
 Ponieważ `End` kończy działanie aplikacji bez udziału w zasobach, które mogą być otwarte, należy spróbować oczyścić się nieprzerwanie przed użyciem. Na przykład jeśli aplikacja ma otwarte jakiekolwiek formularze, należy je zamknąć przed przekroczeniem przez formant `End` .  
  
 Należy używać `End` oszczędnie i tylko wtedy, gdy trzeba natychmiast zatrzymać. Normalne metody kończenia procedury (instrukcja[Return](return-statement.md) i [Exit](exit-statement.md)) nie tylko zamykają procedurę, ale również powodują, że kod wywołujący może czyścić się nieprzerwanie. Aplikacja konsolowa, na przykład, może po prostu wykonać `Return` `Main` procedurę.  
  
> [!IMPORTANT]
> `End`Instrukcja wywołuje <xref:System.Environment.Exit%2A> metodę <xref:System.Environment> klasy w <xref:System> przestrzeni nazw. <xref:System.Environment.Exit%2A>wymaga `UnmanagedCode` uprawnienia. Jeśli tego nie zrobisz, wystąpi <xref:System.Security.SecurityException> błąd.  
  
 Po wykonaniu dodatkowego słowa kluczowego [ \<keyword> instrukcja End](end-keyword-statement.md) wyznacza koniec definicji odpowiedniej procedury lub bloku. Na przykład `End Function` kończy definicję `Function` procedury.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa instrukcji, `End` Aby przerwać wykonywanie kodu, jeśli użytkownik zażąda.  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a>Uwagi dla deweloperów inteligentnych urządzeń  
 Ta instrukcja nie jest obsługiwana.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [Stop, instrukcja](stop-statement.md)
- [End — \<keyword> instrukcja](end-keyword-statement.md)
