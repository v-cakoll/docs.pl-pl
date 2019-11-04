---
title: Jak utworzyć proste powiązanie
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: faef59ed426059eb2d488d0584d3325c8d46d415
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73453510"
---
# <a name="how-to-create-a-simple-binding"></a>Jak utworzyć proste powiązanie
Ten przykład pokazuje, jak utworzyć prostą <xref:System.Windows.Data.Binding>.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie masz `Person` obiekt z właściwością ciągu o nazwie `PersonName`. Obiekt `Person` jest zdefiniowany w przestrzeni nazw o nazwie `SDKSample`.  
  
 Wyróżniony wiersz, który zawiera element `<src>` w poniższym przykładzie tworzy wystąpienie obiektu `Person` z wartością właściwości `PersonName` `Joe`. Należy to zrobić w sekcji `Resources` i przypisać `x:Key`.  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Wyróżniony wiersz zawierający element `<TextBlock>` następnie wiąże formant <xref:System.Windows.Controls.TextBlock> z właściwością `PersonName`. W związku z tym <xref:System.Windows.Controls.TextBlock> pojawia się z wartością "Jan".  
  
## <a name="see-also"></a>Zobacz także

- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
