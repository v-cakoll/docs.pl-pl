---
title: 'Instrukcje: Stosowanie przycinania za pomocą obszaru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regions [Windows Forms], clipping
- regions [Windows Forms], restricting drawing surface
ms.assetid: 43d121b4-e14c-4901-b25c-2d6c25ba4e29
ms.openlocfilehash: cf60b32df805a49f8da2760332dc32e34209f6dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954517"
---
# <a name="how-to-use-clipping-with-a-region"></a>Instrukcje: Stosowanie przycinania za pomocą obszaru
Jedna z właściwości obiektu <xref:System.Drawing.Graphics> klasa jest obszar przycinania. Wszystkie rysunku, wykonywane przez dany <xref:System.Drawing.Graphics> obiektu jest ograniczona do regionu klipu tego <xref:System.Drawing.Graphics> obiektu. Można ustawić obszar przycinania, wywołując <xref:System.Drawing.Graphics.SetClip%2A> metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy ścieżkę, która składa się z pojedynczego wielokąta. Następnie kod tworzy regionu, w oparciu o tej ścieżce. Region jest przekazywany do <xref:System.Drawing.Graphics.SetClip%2A> metody <xref:System.Drawing.Graphics> obiektu, a następnie dwa ciągi są rysowane.  
  
 Poniższa ilustracja przedstawia obciętych ciągów.  
  
 ![Clip](./media/clip1.png "clip1")  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.MiscLegacyTopics#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz także

- [Regiony w GDI+](regions-in-gdi.md)
- [Używanie regionów](using-regions.md)
