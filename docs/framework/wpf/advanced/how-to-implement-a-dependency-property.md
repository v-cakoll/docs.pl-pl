---
title: Jak implementować właściwość zależności
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
ms.openlocfilehash: b0c5b33d841f43249f9559bd31f1ef8fe66ff05e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544651"
---
# <a name="how-to-implement-a-dependency-property"></a>Jak implementować właściwość zależności
W tym przykładzie pokazano, jak utworzyć kopię [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] właściwości o <xref:System.Windows.DependencyProperty> pola, w związku z tym Definiowanie właściwości zależności. Podczas definiowania własnych właściwości i chcesz, aby obsługiwać wiele aspektów [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funkcje, w tym style, powiązanie danych dziedziczenia, animacji i wartości domyślne, należy je zaimplementować jako właściwość zależności.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład najpierw rejestruje właściwości zależności przez wywołanie metody <xref:System.Windows.DependencyProperty.Register%2A> metody. Nazwa pola Identyfikator, który służy do przechowywania nazwy i właściwości właściwości zależności musi być <xref:System.Windows.DependencyProperty.Name%2A> wybrany dla właściwości zależności w ramach <xref:System.Windows.DependencyProperty.Register%2A> wywołanie przez ciąg literału `Property`. Na przykład jeśli Zarejestruj właściwości zależności z <xref:System.Windows.DependencyProperty.Name%2A> z `Location`, następnie pole identyfikatora, dla właściwości zależności musi mieć nazwę `LocationProperty`.  
  
 W tym przykładzie nazwa właściwości zależności i jego [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] akcesor jest `State`; to pole identyfikatora `StateProperty`; typ właściwości jest <xref:System.Boolean>; i typ, który rejestruje właściwość zależności jest `MyStateControl`.  
  
 Jeśli nie należy wykonać ten wzorzec nazewnictwa, projektantów może nie raportować z właściwości prawidłowo i niektórych aspektów aplikacji styl systemu właściwość może nie działać zgodnie z oczekiwaniami.  
  
 Można także określić domyślny metadane dla właściwości zależności. W tym przykładzie rejestruje domyślną wartość `State` właściwości zależności, aby być `false`.  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 Aby uzyskać więcej informacji o tym, jak i dlaczego implementuje właściwości zależności, a nie tylko tworzenie kopii [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] właściwość z polem prywatnych, zobacz [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
