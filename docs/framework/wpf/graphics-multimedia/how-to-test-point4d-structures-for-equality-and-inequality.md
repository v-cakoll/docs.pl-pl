---
title: 'Instrukcje: Testuj struktury Point4D dla równości i nierówności'
ms.date: 03/30/2017
helpviewer_keywords:
- inequality [WPF], testing Point4D structures for
- equality [WPF], testing Point4D structures for
- testing [WPF], Point4D structures for equality
- Point4D structures [WPF], testing for inequality
- testing [WPF], Point4D structures for inequality
- Point4D structures [WPF], testing for equality
ms.assetid: e004a67e-db7f-4af8-a31f-e6b2a44ccf34
ms.openlocfilehash: 1366f66a54266aaae61baf1cf6eee9792da732f7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724531"
---
# <a name="how-to-test-point4d-structures-for-equality-and-inequality"></a>Instrukcje: Testuj struktury Point4D dla równości i nierówności
W tym przykładzie pokazano, jak przetestować <xref:System.Windows.Media.Media3D.Point4D> struktury pod kątem równości i nierówności.  
  
 Poniższy kod ilustruje sposób testowania <xref:System.Windows.Media.Media3D.Point4D> struktury dla równości i nierówności przy użyciu <xref:System.Windows.Media.Media3D.Point4D> metody porównania.  <xref:System.Windows.Media.Media3D.Point4D> Struktury są testowane na równość za pomocą przeciążonych równości (`==`) operator, następnie pod kątem nierówności przy użyciu przeciążonych nierówności (`!=`) operator, a na koniec <xref:System.Windows.Media.Media3D.Point3D> struktury i <xref:System.Windows.Media.Media3D.Point4D> struktury są sprawdzane pod kątem równości, przy użyciu statycznych <xref:System.Windows.Media.Media3D.Point4D.Equals%2A> metody.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[3DGallery_procedural_snip#Point4DEqualityExample_csharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Misc3DOperationsExample.cs#point4dequalityexample_csharp)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.Media3D.Point4D.op_Equality%2A>
- <xref:System.Windows.Media.Media3D.Point4D.op_Inequality%2A>
- <xref:System.Windows.Media.Media3D.Point4D.Equals%2A>
