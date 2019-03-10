---
title: 'Instrukcje: Użyj testowania trafień za pomocą obszaru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [Windows Forms], using regions
- regions [Windows Forms], hit testing
ms.assetid: 3a4c07cb-a40a-4d14-ad35-008f531910a8
ms.openlocfilehash: a9435724e7674fd196ad70bdfd0ab43808a53058
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709755"
---
# <a name="how-to-use-hit-testing-with-a-region"></a>Instrukcje: Użyj testowania trafień za pomocą obszaru
Testowanie trafień ma na celu określenia, czy kursor znajduje się za pośrednictwem danego obiektu, takie jak ikony lub przycisku.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy obszar ukształtowane plus tworzymy sumę dwóch regionach prostokątny. Przyjęto założenie, że zmienna `point` jest przechowywana lokalizacja kliknij najbardziej aktualne. Kod sprawdza, czy `point` znajduje się w regionie kształcie na znak plus. Jeśli punkt znajduje się w regionie (naciśnij klawisz), region jest wypełniony nieprzezroczyste pędzla czerwony. W przeciwnym razie region jest wypełniony półprzezroczystych pędzli czerwony.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.MiscLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Drawing.Region>
- [Regiony w GDI+](regions-in-gdi.md)
- [Instrukcje: Stosowanie przycinania za pomocą obszaru](how-to-use-clipping-with-a-region.md)
