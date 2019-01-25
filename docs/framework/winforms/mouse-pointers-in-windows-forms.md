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
ms.openlocfilehash: 02f93a85ecaa13f5f72cd0f31a1f5ffc24c59f68
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491782"
---
# <a name="mouse-pointers-in-windows-forms"></a>Wskaźniki myszy w formularzach systemu Windows
Wskaźnik myszy *wskaźnika*, który jest czasami nazywany kursora, jest mapę bitową, która określa punkt koncentracji uwagi na ekranie dla danych wejściowych użytkownika za pomocą myszy. Ten temat zawiera omówienie wskaźnik myszy w formularzach Windows Forms i opisuje kilka sposobów modyfikowania i sterowanie wskaźnikiem myszy.  
  
## <a name="accessing-the-mouse-pointer"></a>Uzyskiwanie dostępu do wskaźnika myszy  
 Wskaźnik myszy jest reprezentowany przez <xref:System.Windows.Forms.Cursor> klasy, a każda <xref:System.Windows.Forms.Control> ma <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> właściwość, która określa wskaźnik dla tej kontrolki. <xref:System.Windows.Forms.Cursor> Klasa zawiera właściwości, które opisują wskaźnika, takich jak <xref:System.Windows.Forms.Cursor.Position%2A> i <xref:System.Windows.Forms.Cursor.HotSpot%2A> właściwości i metod, które można modyfikować wygląd wskaźnika, takich jak <xref:System.Windows.Forms.Cursor.Show%2A>, <xref:System.Windows.Forms.Cursor.Hide%2A>, i <xref:System.Windows.Forms.Cursor.DrawStretched%2A> metody.  
  
## <a name="controlling-the-mouse-pointer"></a>Kontrolowanie wskaźnika myszy  
 Czasami warto ograniczyć obszar, w którym wskaźnik myszy mogą być używane, lub zmienić położenie myszy. Można pobrać lub ustawić bieżącą lokalizację przy użyciu myszy <xref:System.Windows.Forms.Cursor.Position%2A> właściwość <xref:System.Windows.Forms.Cursor>. Ponadto, można ograniczyć obszar może służyć wskaźnik myszy jest ustawienie <xref:System.Windows.Forms.Cursor.Clip%2A> właściwości. Obszar klipu, domyślnie jest cały ekran.  
  
## <a name="changing-the-mouse-pointer"></a>Zmienianie wskaźnika myszy  
 Zmiana wskaźnik myszy jest istotnym sposobem udostępniania opinii użytkownika. Na przykład, można zmodyfikować wskaźnik myszy w procedurach obsługi z <xref:System.Windows.Forms.Control.MouseEnter> i <xref:System.Windows.Forms.Control.MouseLeave> zdarzeń, aby poinformować użytkownika występują obliczeń i ograniczać interakcji z użytkownikiem w formancie. Czasami wskaźnik myszy zmieni się z powodu zdarzenia systemowe, takie jak kiedy aplikacja jest zaangażowana w operację przeciągania i upuszczania.  
  
 Podstawowym sposobem, aby zmienić wskaźnik myszy jest ustawiając <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> lub <xref:System.Windows.Forms.Control.DefaultCursor%2A> właściwości formantu do nowego <xref:System.Windows.Forms.Cursor>. Przykłady Zmienianie wskaźnika myszy można znaleźć w przykładzie kodu w <xref:System.Windows.Forms.Cursor> klasy. Ponadto <xref:System.Windows.Forms.Cursors> klasa udostępnia zestaw <xref:System.Windows.Forms.Cursor> obiektów dla wielu różnych wskaźników, takie jak wskaźnik, który przypomina dłoni. Aby wyświetlić wskaźnik oczekiwania, który przypomina Klepsydra zawsze wtedy, gdy wskaźnik myszy na kontrolce, należy użyć <xref:System.Windows.Forms.Control.UseWaitCursor%2A> właściwość <xref:System.Windows.Forms.Control> klasy.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.Cursor>
- [Wprowadzanie za pomocą myszy w aplikacjach Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
- [Funkcjonalność przeciągania i upuszczania w formularzach Windows Forms](../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)
