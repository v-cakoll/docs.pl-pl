---
title: 'Instrukcje: Tworzenie przycisku mającego obraz'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Button controls [WPF], creating
ms.assetid: 607a193c-4098-4dd8-8dc0-51256cec2020
ms.openlocfilehash: 5be928ac75ad727feabcde07ac0c6dc76ed130e6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120726"
---
# <a name="how-to-create-a-button-that-has-an-image"></a>Instrukcje: Tworzenie przycisku mającego obraz
W tym przykładzie pokazano jak dołączyć obraz na <xref:System.Windows.Controls.Button>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy dwie <xref:System.Windows.Controls.Button> kontrolki. Jeden <xref:System.Windows.Controls.Button> zawiera tekst, a drugi zawiera obraz. Obraz, który znajduje się w folderze o nazwie danych, który jest podfolderem folderu projektu w przykładzie. Kiedy użytkownik kliknie <xref:System.Windows.Controls.Button> zawierającego obraz tła i tekstu z innych <xref:System.Windows.Controls.Button> zmiany.  
  
 Ten przykład tworzy <xref:System.Windows.Controls.Button> steruje się za pomocą znaczników, ale używa kodu, aby zapisać <xref:System.Windows.Controls.Primitives.ButtonBase.Click> procedury obsługi zdarzeń.  
  
 [!code-xaml[BtnColor#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml#4)]  
  
 [!code-csharp[BtnColor#6](~/samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml.cs#6)]
 [!code-vb[BtnColor#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BtnColor/VisualBasic/Pane1.xaml.vb#6)]  
  
## <a name="see-also"></a>Zobacz także

- [Formanty](index.md)
- [Biblioteka formantów](control-library.md)
