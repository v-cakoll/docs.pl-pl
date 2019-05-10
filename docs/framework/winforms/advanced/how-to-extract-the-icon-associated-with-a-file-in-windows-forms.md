---
title: 'Instrukcje: Wyodrębnianie ikon skojarzonych z plikiem w formularzach systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
ms.openlocfilehash: c3173a3fa756a3294154217f5cf0a13dbc8721f3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645400"
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a>Instrukcje: Wyodrębnianie ikon skojarzonych z plikiem w formularzach systemu Windows
Wiele plików zostały osadzone ikon, które zapewniają wizualnej reprezentacji skojarzonego typu pliku. Na przykład dokumenty Microsoft Word zawiera ikonę która identyfikuje je jako dokumenty programu Word. Wyświetlanie plików w formancie listy lub kontrolki tabeli, można wyświetlić ikony reprezentującej typ pliku obok nazwy każdego pliku. Łatwo to zrobić, korzystając z <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak wyodrębnianie ikon skojarzonych z plikiem i wyświetlić nazwę pliku i jego skojarzonej ikony w <xref:System.Windows.Forms.ListView> kontroli.  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować przykład:  
  
- Wklej powyższy kod do formularza Windows i Wywołaj `ExtractAssociatedIconExample` metody z konstruktora formularza lub <xref:System.Windows.Forms.Form.Load> metody obsługi zdarzeń.  
  
     Należy się upewnić, że formularz importuje <xref:System.IO> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- [Obrazy, mapy bitowe i metapliki](images-bitmaps-and-metafiles.md)
- [Kontrolka ListView](../controls/listview-control-windows-forms.md)
