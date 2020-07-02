---
title: Jak utworzyć proste powiązanie
description: Utwórz proste powiązanie dla aplikacji za pomocą tego przykładu w Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 63dc44b442bb4658382bf12faf57b51c8e0698bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618704"
---
# <a name="how-to-create-a-simple-binding"></a>Jak utworzyć proste powiązanie
Ten przykład pokazuje, jak utworzyć prostą <xref:System.Windows.Data.Binding> .  
  
## <a name="example"></a>Przykład  
 W tym przykładzie masz `Person` obiekt z właściwością ciągu o nazwie `PersonName` . `Person`Obiekt jest zdefiniowany w przestrzeni nazw o nazwie `SDKSample` .  
  
 Wyróżniony wiersz, który zawiera `<src>` element w poniższym przykładzie tworzy wystąpienie `Person` obiektu z `PersonName` wartością właściwości `Joe` . Jest to wykonywane w `Resources` sekcji i przypisane `x:Key` .  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Wyróżniony wiersz, który zawiera `<TextBlock>` element, następnie wiąże <xref:System.Windows.Controls.TextBlock> formant z `PersonName` właściwością. W rezultacie <xref:System.Windows.Controls.TextBlock> pojawia się wartość "Jan".  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd powiązań danych](../../../desktop-wpf/data/data-binding-overview.md)
- [— Tematy porad](data-binding-how-to-topics.md)
