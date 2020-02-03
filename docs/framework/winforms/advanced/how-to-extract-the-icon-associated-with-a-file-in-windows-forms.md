---
title: 'Instrukcje: Wyodrębnianie ikony skojarzonej z plikiem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
ms.openlocfilehash: 28769144b0e1c631a31c3c541747a6215f861d0e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742543"
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a>Porady: wyodrębnianie ikon skojarzonych z plikiem w formularzach systemu Windows
Wiele plików ma osadzone ikony, które zapewniają wizualną reprezentację skojarzonego typu pliku. Na przykład dokumenty programu Microsoft Word zawierają ikonę, która identyfikuje je jako dokumenty programu Word. Podczas wyświetlania plików w kontrolce listy lub formancie tabeli można wyświetlić ikonę reprezentującą typ pliku obok każdej nazwy pliku. Można to łatwo zrobić przy użyciu metody <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje, jak wyodrębnić ikonę skojarzoną z plikiem i wyświetlić nazwę pliku oraz skojarzoną ikonę w kontrolce <xref:System.Windows.Forms.ListView>.  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować przykład:  
  
- Wklej poprzedni kod do formularza systemu Windows i Wywołaj metodę `ExtractAssociatedIconExample` z konstruktora formularza lub <xref:System.Windows.Forms.Form.Load> metody obsługi zdarzeń.  
  
     Należy upewnić się, że formularz importuje <xref:System.IO> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- [Obrazy, mapy bitowe i metapliki](images-bitmaps-and-metafiles.md)
- [Kontrolka ListView](../controls/listview-control-windows-forms.md)
