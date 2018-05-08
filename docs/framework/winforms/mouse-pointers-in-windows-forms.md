---
title: Wskaźniki myszy w formularzach systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- pointers [Windows Forms], setting
- mouse pointers
- mouse cursors
- mouse pointers [Windows Forms], setting
- cursors [Windows Forms], setting
- mouse [Windows Forms], cursors
ms.assetid: c3400d85-de5b-42e8-abc3-d6088d69ee53
ms.openlocfilehash: ed6312cb386d1557d4217a330318664b4e87c330
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="mouse-pointers-in-windows-forms"></a>Wskaźniki myszy w formularzach systemu Windows
Mysz *wskaźnika*, który jest czasami nazywany kursor jest mapą bitową, określająca fokus na ekranie dla danych wejściowych użytkownika przy użyciu myszy. Ten temat zawiera omówienie wskaźnik myszy w formularzach systemu Windows oraz opis niektórych sposobów, aby zmodyfikować i kontrolować wskaźnik myszy.  
  
## <a name="accessing-the-mouse-pointer"></a>Uzyskiwanie dostępu do wskaźnika myszy  
 Wskaźnik myszy jest reprezentowana przez <xref:System.Windows.Forms.Cursor> klasy, a każdy <xref:System.Windows.Forms.Control> ma <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> właściwość, która określa wskaźnik dla tego formantu. <xref:System.Windows.Forms.Cursor> Klasy zawiera właściwości, które opisują wskaźnika, takich jak <xref:System.Windows.Forms.Cursor.Position%2A> i <xref:System.Windows.Forms.Cursor.HotSpot%2A> właściwości i metody, które można zmodyfikować wygląd kursora, takich jak <xref:System.Windows.Forms.Cursor.Show%2A>, <xref:System.Windows.Forms.Cursor.Hide%2A>, i <xref:System.Windows.Forms.Cursor.DrawStretched%2A> metody.  
  
## <a name="controlling-the-mouse-pointer"></a>Kontrolowanie wskaźnika myszy  
 Czasami można ograniczyć obszar, w którym wskaźnik myszy mogą być używane, lub zmienić jego położenie myszy. Można pobrać lub ustawić bieżącą lokalizację przy użyciu myszy <xref:System.Windows.Forms.Cursor.Position%2A> właściwość <xref:System.Windows.Forms.Cursor>. Ponadto można ograniczyć obszar może służyć wskaźnik myszy jest ustawienie <xref:System.Windows.Forms.Cursor.Clip%2A> właściwości. Obszar przycinania, domyślnie jest cały ekran.  
  
## <a name="changing-the-mouse-pointer"></a>Zmienianie wskaźnika myszy  
 Zmiana wskaźnik myszy jest istotnym sposobem zapewnienia opinii dla użytkownika. Na przykład można zmodyfikować wskaźnik myszy w obsłudze programu <xref:System.Windows.Forms.Control.MouseEnter> i <xref:System.Windows.Forms.Control.MouseLeave> zdarzeń użytkownika stwierdzić, że obliczenia są wykonywane i ograniczać interakcji z użytkownikiem w formancie. Czasami wskaźnik myszy zmieni się z powodu zdarzenia systemowe, np. gdy aplikacja uczestniczy w operacji przeciągania i upuszczania.  
  
 Podstawowy sposobem zmienić wskaźnik myszy jest ustawienie <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> lub <xref:System.Windows.Forms.Control.DefaultCursor%2A> właściwości formantu na nowy <xref:System.Windows.Forms.Cursor>. Przykłady zmiana wskaźnik myszy można znaleźć przykładowy kod z <xref:System.Windows.Forms.Cursor> klasy. Ponadto <xref:System.Windows.Forms.Cursors> klasy udostępnia zestaw <xref:System.Windows.Forms.Cursor> obiektów dla wielu różnych typów wskaźników, takich jak wskaźnik podobny dłoni. Aby wyświetlić wskaźnika oczekiwania podobny Klepsydra zawsze, gdy wskaźnik myszy znajduje się w formancie, należy użyć <xref:System.Windows.Forms.Control.UseWaitCursor%2A> właściwość <xref:System.Windows.Forms.Control> klasy.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Cursor>  
 [Wprowadzanie za pomocą myszy w aplikacjach Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)  
 [Funkcjonalność przeciągania i upuszczania w formularzach Windows Forms](../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)
