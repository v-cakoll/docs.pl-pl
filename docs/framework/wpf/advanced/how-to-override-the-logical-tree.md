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
ms.workload: dotnet
ms.openlocfilehash: e487220f8b06515f3d37f7d55ab7ff6214c85d92
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-override-the-logical-tree"></a>Jak zastąpić drzewo logiczne
Chociaż nie jest konieczne w większości przypadków, autorzy formantu zaawansowanego istnieje możliwość zastąpienia drzewa logicznego.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono sposób podklasy <xref:System.Windows.Controls.StackPanel> do zastąpienia drzewo logiczne, w tym przypadku aby wymusić zachowanie czy panelu może mieć tylko i będzie renderować obraz tylko pojedynczym elemencie podrzędnym. To nie zawsze jest praktycznie pożądane zachowanie, ale podano tutaj jako środek pokazujący scenariusz dotyczący przesłonięcia elementu normalne drzewa logicznego.  
  
 [!code-csharp[LogicalOverride#SingletonPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 Aby uzyskać więcej informacji na drzewie logicznym, zobacz [drzewa WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).
