---
title: Jak utworzyć proste powiązanie
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 8910dd3ec6c9f72f9d8fb64cd33912f0d4318e5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-simple-binding"></a>Jak utworzyć proste powiązanie
W tym przykładzie przedstawiono sposób tworzenia prostej <xref:System.Windows.Data.Binding>.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie należy `Person` obiektu z właściwością ciągu o nazwie `PersonName`. `Person` Obiektu jest zdefiniowana w obszarze nazw o nazwie `SDKSample`.  
  
 Wyróżniony wiersz, który zawiera `<src>` tworzy wystąpienie elementu w poniższym przykładzie `Person` obiekt z `PersonName` wartość właściwości `Joe`. Jest to wykonywane w `Resources` sekcji i przypisaniu `x:Key`.  
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Wyróżniony wiersz, który zawiera `<TextBlock>` element czym wiąże <xref:System.Windows.Controls.TextBlock> formant `PersonName` właściwości. W związku z tym <xref:System.Windows.Controls.TextBlock> pojawi się o wartości "Jan".  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
