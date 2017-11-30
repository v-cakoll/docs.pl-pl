---
title: "Jak testować struktury Point4D dla równości i nierówności"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inequality [WPF], testing Point4D structures for
- equality [WPF], testing Point4D structures for
- testing [WPF], Point4D structures for equality
- Point4D structures [WPF], testing for inequality
- testing [WPF], Point4D structures for inequality
- Point4D structures [WPF], testing for equality
ms.assetid: e004a67e-db7f-4af8-a31f-e6b2a44ccf34
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 849082fc1b933c4172c0d22ec3c9c2a1644a32fb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-test-point4d-structures-for-equality-and-inequality"></a>Jak testować struktury Point4D dla równości i nierówności
W tym przykładzie pokazano, jak przetestować <xref:System.Windows.Media.Media3D.Point4D> struktur równości i nierówności.  
  
 Poniższy kod ilustruje sposób przetestować <xref:System.Windows.Media.Media3D.Point4D> struktur równości i nierówności przy użyciu <xref:System.Windows.Media.Media3D.Point4D> metody równości.  <xref:System.Windows.Media.Media3D.Point4D> Struktury są sprawdzane pod kątem równości przy użyciu przeciążone równości (`==`) operatora, następnie pod kątem nierówności przy użyciu przeciążone nierówności (`!=`) operatora, a na końcu <xref:System.Windows.Media.Media3D.Point3D> struktury i <xref:System.Windows.Media.Media3D.Point4D> Struktura są sprawdzane pod kątem równości przy użyciu statycznych <xref:System.Windows.Media.Media3D.Point4D.Equals%2A> metody.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[3DGallery_procedural_snip#Point4DEqualityExample_csharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Misc3DOperationsExample.cs#point4dequalityexample_csharp)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Media3D.Point4D.op_Equality%2A>  
 <xref:System.Windows.Media.Media3D.Point4D.op_Inequality%2A>  
 <xref:System.Windows.Media.Media3D.Point4D.Equals%2A>
