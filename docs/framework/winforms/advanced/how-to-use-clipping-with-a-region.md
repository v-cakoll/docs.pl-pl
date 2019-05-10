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
ms.openlocfilehash: e62be137b36a2f369c02151466154f6b3bab090b
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063838"
---
# <a name="how-to-use-clipping-with-a-region"></a>Instrukcje: Stosowanie przycinania za pomocą obszaru
Jedna z właściwości obiektu <xref:System.Drawing.Graphics> klasa jest obszar przycinania. Wszystkie rysunku, wykonywane przez dany <xref:System.Drawing.Graphics> obiektu jest ograniczona do regionu klipu tego <xref:System.Drawing.Graphics> obiektu. Można ustawić obszar przycinania, wywołując <xref:System.Drawing.Graphics.SetClip%2A> metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy ścieżkę, która składa się z pojedynczego wielokąta. Następnie kod tworzy regionu, w oparciu o tej ścieżce. Region jest przekazywany do <xref:System.Drawing.Graphics.SetClip%2A> metody <xref:System.Drawing.Graphics> obiektu, a następnie dwa ciągi są rysowane.  
  
 Poniższa ilustracja przedstawia obciętych ciągów:  
  
 ![Zrzut ekranu pokazujący obciętych ciągów.](./media/how-to-use-clipping-with-a-region/clipped-strings-polygon.png)  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.MiscLegacyTopics#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz także

- [Regiony w GDI+](regions-in-gdi.md)
- [Używanie regionów](using-regions.md)
