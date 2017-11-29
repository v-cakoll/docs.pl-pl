---
title: "Jak zastąpić drzewo logiczne"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- overriding the logical tree [WPF]
- logical tree [WPF], overriding
ms.assetid: 0ae4d074-8113-4b06-b4fa-e0f39d4967a6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4cc6045d3505981d93f07347ebd49d57cd759774
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-override-the-logical-tree"></a>Jak zastąpić drzewo logiczne
Chociaż nie jest konieczne w większości przypadków, autorzy formantu zaawansowanego istnieje możliwość zastąpienia drzewa logicznego.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono sposób podklasy <xref:System.Windows.Controls.StackPanel> do zastąpienia drzewo logiczne, w tym przypadku aby wymusić zachowanie czy panelu może mieć tylko i będzie renderować obraz tylko pojedynczym elemencie podrzędnym. To nie zawsze jest praktycznie pożądane zachowanie, ale podano tutaj jako środek pokazujący scenariusz dotyczący przesłonięcia elementu normalne drzewa logicznego.  
  
 [!code-csharp[LogicalOverride#SingletonPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 Aby uzyskać więcej informacji na drzewie logicznym, zobacz [drzewa WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).
