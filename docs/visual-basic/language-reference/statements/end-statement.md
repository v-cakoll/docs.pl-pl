---
title: "End — Instrukcja"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b692409f2895f5e9b713c57fc35ff2def40bce75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="end-statement"></a>End — Instrukcja
Kończy wykonywanie natychmiast.  
  
## <a name="syntax"></a>Składnia  
  
```  
End  
```  
  
## <a name="remarks"></a>Uwagi  
 Możesz umieścić `End` instrukcji w dowolnym miejscu procedury, aby wymusić cała aplikacja przestanie działać. `End`Zamyka wszystkie pliki otwarte z `Open` instrukcji i czyści zmienne wszystkich aplikacji. Aplikacja zamyka nie ma żadnych innych programów zawierający odniesienia do swoich obiektów, a nie działa żadna jego kod.  
  
> [!NOTE]
>  `End` Instrukcji nagle zatrzymuje wykonywanie kodu i nie jest wywoływany `Dispose` lub `Finalize` metody lub inny kod Visual Basic. Odwołania do obiektów przechowywanych przez inne programy są unieważniona. Jeśli `End` napotkano w instrukcji `Try` lub `Catch` bloku, formantu nie przekazuje do odpowiadającego `Finally` bloku.  
  
 `Stop` Instrukcji wstrzymuje wykonywanie, lecz w przeciwieństwie do `End`, zamknij wszystkie pliki lub nie wyczyść wszystkie zmienne, chyba że jest wystąpił w pliku skompilowanego pliku wykonywalnego (.exe).  
  
 Ponieważ `End` kończy aplikacji bez uczestnictwa do żadnych zasobów, które mogą być otwarte, należy spróbować wstrzymuje prawidłowo, przed jego użyciem. Na przykład jeśli aplikacja ma Otwórz formularzy, należy zamknąć je przed osiągnie kontroli `End` instrukcji.  
  
 Należy używać `End` oszczędnie i tylko kiedy należy zatrzymać natychmiast. Normalne sposoby zakończyć procedurę ([zwracać instrukcji](../../../visual-basic/language-reference/statements/return-statement.md) i [instrukcji Zakończ](../../../visual-basic/language-reference/statements/exit-statement.md)) nie tylko prawidłowo zamknięcia procedurą, ale również dawać kod wywołujący możliwość wstrzymuje prawidłowo. Aplikacji konsoli, na przykład można po prostu `Return` z `Main` procedury.  
  
> [!IMPORTANT]
>  `End` Wywołania instrukcji <xref:System.Environment.Exit%2A> metody <xref:System.Environment> klasy w <xref:System> przestrzeni nazw. <xref:System.Environment.Exit%2A>Musisz mieć `UnmanagedCode` uprawnienia. Jeśli nie, <xref:System.Security.SecurityException> wystąpi błąd.  
  
 Gdy następuje dodatkowe — słowo kluczowe [zakończenia \<— słowo kluczowe > instrukcji](../../../visual-basic/language-reference/statements/end-keyword-statement.md) wyznacza koniec definicji odpowiednią procedurę lub blok. Na przykład `End Function` kończy definicję `Function` procedury.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `End` instrukcji, aby zakończyć wykonywanie kodu, jeśli użytkownik zażąda tego.  
  
 [!code-vb[VbVersHelp60Controls#64](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/end-statement_1.vb)]  
  
## <a name="smart-device-developer-notes"></a>Uwagi dla deweloperów inteligentnych urządzeń  
 Ta instrukcja nie jest obsługiwana.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.Permissions.SecurityPermissionFlag>  
 [Stop — instrukcja](../../../visual-basic/language-reference/statements/stop-statement.md)  
 [Końcowy \<— słowo kluczowe > — instrukcja](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
