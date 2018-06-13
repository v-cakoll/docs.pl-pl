---
title: Jak zastąpić drzewo logiczne
ms.date: 03/30/2017
helpviewer_keywords:
- overriding the logical tree [WPF]
- logical tree [WPF], overriding
ms.assetid: 0ae4d074-8113-4b06-b4fa-e0f39d4967a6
ms.openlocfilehash: 0c7269b9ea052019e2e4f6def23b063903cbb5e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542893"
---
# <a name="how-to-override-the-logical-tree"></a>Jak zastąpić drzewo logiczne
Chociaż nie jest konieczne w większości przypadków, autorzy formantu zaawansowanego istnieje możliwość zastąpienia drzewa logicznego.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono sposób podklasy <xref:System.Windows.Controls.StackPanel> do zastąpienia drzewo logiczne, w tym przypadku aby wymusić zachowanie czy panelu może mieć tylko i będzie renderować obraz tylko pojedynczym elemencie podrzędnym. To nie zawsze jest praktycznie pożądane zachowanie, ale podano tutaj jako środek pokazujący scenariusz dotyczący przesłonięcia elementu normalne drzewa logicznego.  
  
 [!code-csharp[LogicalOverride#SingletonPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 Aby uzyskać więcej informacji na drzewie logicznym, zobacz [drzewa WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).
