---
title: Wskaźniki myszy
ms.date: 03/30/2017
helpviewer_keywords:
- pointers [Windows Forms], setting
- mouse pointers
- mouse cursors
- mouse pointers [Windows Forms], setting
- cursors [Windows Forms], setting
- mouse [Windows Forms], cursors
ms.assetid: c3400d85-de5b-42e8-abc3-d6088d69ee53
ms.openlocfilehash: 4e8349effcd9b59045e39b763b4cb8b7d2fceb91
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740959"
---
# <a name="mouse-pointers-in-windows-forms"></a>Wskaźniki myszy w formularzach systemu Windows
*Wskaźnik*myszy, który jest czasami nazywany kursorem, jest mapą bitową, która określa punkt fokusu na ekranie dla danych wejściowych użytkownika za pomocą myszy. Ten temat zawiera omówienie wskaźnika myszy w Windows Forms i opisuje niektóre sposoby modyfikowania i kontrolowania wskaźnika myszy.  
  
## <a name="accessing-the-mouse-pointer"></a>Uzyskiwanie dostępu do wskaźnika myszy  
 Wskaźnik myszy jest reprezentowany przez klasę <xref:System.Windows.Forms.Cursor>, a każda <xref:System.Windows.Forms.Control> ma właściwość <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType>, która określa wskaźnik dla tej kontrolki. Klasa <xref:System.Windows.Forms.Cursor> zawiera właściwości opisujące wskaźnik, takie jak właściwości <xref:System.Windows.Forms.Cursor.Position%2A> i <xref:System.Windows.Forms.Cursor.HotSpot%2A> oraz metody, które mogą modyfikować wygląd wskaźnika, takie jak <xref:System.Windows.Forms.Cursor.Show%2A>, <xref:System.Windows.Forms.Cursor.Hide%2A>i metody <xref:System.Windows.Forms.Cursor.DrawStretched%2A>.  
  
## <a name="controlling-the-mouse-pointer"></a>Kontrolowanie wskaźnika myszy  
 Czasami może być konieczne ograniczenie obszaru, w którym można użyć wskaźnika myszy, lub zmienić położenie myszy. Bieżącą lokalizację myszy można pobrać lub ustawić przy użyciu właściwości <xref:System.Windows.Forms.Cursor.Position%2A> <xref:System.Windows.Forms.Cursor>. Ponadto można ograniczyć obszar, w którym można użyć wskaźnika myszy, aby ustawić właściwość <xref:System.Windows.Forms.Cursor.Clip%2A>. Domyślnie obszar przycinania to cały ekran.  
  
## <a name="changing-the-mouse-pointer"></a>Zmiana wskaźnika myszy  
 Zmiana wskaźnika myszy jest ważnym sposobem przekazywania użytkownikowi opinii. Na przykład można zmodyfikować wskaźnik myszy w obsłudze zdarzeń <xref:System.Windows.Forms.Control.MouseEnter> i <xref:System.Windows.Forms.Control.MouseLeave>, aby poinformować użytkownika, że obliczenia są wykonywane i ograniczyć interakcję użytkownika w formancie. Czasami wskaźnik myszy ulegnie zmianie ze względu na zdarzenia systemowe, takie jak w przypadku, gdy aplikacja jest używana w operacji przeciągania i upuszczania.  
  
 Podstawowym sposobem zmiany wskaźnika myszy jest ustawienie właściwości <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> lub <xref:System.Windows.Forms.Control.DefaultCursor%2A> kontrolki na nowy <xref:System.Windows.Forms.Cursor>. Aby uzyskać przykłady zmiany wskaźnika myszy, zobacz przykład kodu w klasie <xref:System.Windows.Forms.Cursor>. Ponadto Klasa <xref:System.Windows.Forms.Cursors> uwidacznia zestaw obiektów <xref:System.Windows.Forms.Cursor> dla wielu różnych typów wskaźników, takich jak wskaźnik przypominający dłoń. Aby wyświetlić wskaźnik oczekiwania, który przypomina klepsydrę, za każdym razem, gdy wskaźnik myszy znajduje się na kontrolce, użyj właściwości <xref:System.Windows.Forms.Control.UseWaitCursor%2A> klasy <xref:System.Windows.Forms.Control>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Cursor>
- [Wprowadzanie za pomocą myszy w aplikacjach Windows Forms](mouse-input-in-a-windows-forms-application.md)
- [Funkcjonalność przeciągania i upuszczania w formularzach Windows Forms](drag-and-drop-functionality-in-windows-forms.md)
