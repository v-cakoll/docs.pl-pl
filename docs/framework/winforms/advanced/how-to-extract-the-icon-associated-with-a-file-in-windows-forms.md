---
title: 'Porady: wyodrębnianie ikon skojarzonych z plikiem w formularzach systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
ms.openlocfilehash: 21bce2f630649afb59272362a7f40055855ed512
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a>Porady: wyodrębnianie ikon skojarzonych z plikiem w formularzach systemu Windows
Wiele plików zostały osadzone ikony, które pozwalają wizualną reprezentację skojarzonego typu pliku. Na przykład Microsoft Word dokumenty zawierają ikonę, która identyfikuje je jako dokumenty programu Word. Wyświetlanie plików w formancie listy lub formancie tabeli, możesz wyświetlić ikonę reprezentujący typ pliku obok nazwy każdego pliku. Łatwo to zrobić, za pomocą <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> metody.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak wyodrębnianie ikon skojarzonych z plikiem i wyświetlić nazwę pliku i jego skojarzony ikonę w <xref:System.Windows.Forms.ListView> formantu.  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować w przykładzie:  
  
-   Wklej poprzedni kod w formularzu systemu Windows, a wywołania `ExtractAssociatedIconExample` metody z Konstruktor elementu form lub <xref:System.Windows.Forms.Form.Load> metoda obsługi zdarzeń.  
  
     Należy się upewnić, że formularz importuje <xref:System.IO> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też  
 [Obrazy, mapy bitowe i metapliki](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Kontrolka ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
