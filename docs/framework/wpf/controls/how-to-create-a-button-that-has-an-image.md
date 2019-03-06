---
title: 'Instrukcje: Utwórz przycisk, który posiada obraz'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Button controls [WPF], creating
ms.assetid: 607a193c-4098-4dd8-8dc0-51256cec2020
ms.openlocfilehash: fe9f35a6f83c5a839823d94c4d3c55e01b192fb1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352038"
---
# <a name="how-to-create-a-button-that-has-an-image"></a>Instrukcje: Utwórz przycisk, który posiada obraz
W tym przykładzie pokazano jak dołączyć obraz na <xref:System.Windows.Controls.Button>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy dwie <xref:System.Windows.Controls.Button> kontrolki. Jeden <xref:System.Windows.Controls.Button> zawiera tekst, a drugi zawiera obraz. Obraz, który znajduje się w folderze o nazwie danych, który jest podfolderem folderu projektu w przykładzie. Kiedy użytkownik kliknie <xref:System.Windows.Controls.Button> zawierającego obraz tła i tekstu z innych <xref:System.Windows.Controls.Button> zmiany.  
  
 Ten przykład tworzy <xref:System.Windows.Controls.Button> steruje się za pomocą znaczników, ale używa kodu, aby zapisać <xref:System.Windows.Controls.Primitives.ButtonBase.Click> procedury obsługi zdarzeń.  
  
 [!code-xaml[BtnColor#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml#4)]  
  
 [!code-csharp[BtnColor#6](~/samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml.cs#6)]
 [!code-vb[BtnColor#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BtnColor/VisualBasic/Pane1.xaml.vb#6)]  
  
## <a name="see-also"></a>Zobacz także
- [Kontrolki](index.md)
- [Biblioteka kontrolek](control-library.md)
