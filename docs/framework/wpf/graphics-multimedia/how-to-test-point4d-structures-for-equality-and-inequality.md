---
title: Jak testować struktury Point4D dla równości i nierówności
ms.date: 03/30/2017
helpviewer_keywords:
- inequality [WPF], testing Point4D structures for
- equality [WPF], testing Point4D structures for
- testing [WPF], Point4D structures for equality
- Point4D structures [WPF], testing for inequality
- testing [WPF], Point4D structures for inequality
- Point4D structures [WPF], testing for equality
ms.assetid: e004a67e-db7f-4af8-a31f-e6b2a44ccf34
ms.openlocfilehash: 1ec844c8fb0aceaaec6030c2e9d5cb30cf984f43
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-test-point4d-structures-for-equality-and-inequality"></a><span data-ttu-id="c49a3-102">Jak testować struktury Point4D dla równości i nierówności</span><span class="sxs-lookup"><span data-stu-id="c49a3-102">How to: Test Point4D structures for equality and inequality</span></span>
<span data-ttu-id="c49a3-103">W tym przykładzie pokazano, jak przetestować <xref:System.Windows.Media.Media3D.Point4D> struktur równości i nierówności.</span><span class="sxs-lookup"><span data-stu-id="c49a3-103">This example shows how to test <xref:System.Windows.Media.Media3D.Point4D> structures for equality and inequality.</span></span>  
  
 <span data-ttu-id="c49a3-104">Poniższy kod ilustruje sposób przetestować <xref:System.Windows.Media.Media3D.Point4D> struktur równości i nierówności przy użyciu <xref:System.Windows.Media.Media3D.Point4D> metody równości.</span><span class="sxs-lookup"><span data-stu-id="c49a3-104">The following code illustrates how to test <xref:System.Windows.Media.Media3D.Point4D> structures for equality and inequality using the <xref:System.Windows.Media.Media3D.Point4D> equality methods.</span></span>  <span data-ttu-id="c49a3-105"><xref:System.Windows.Media.Media3D.Point4D> Struktury są sprawdzane pod kątem równości przy użyciu przeciążone równości (`==`) operatora, następnie pod kątem nierówności przy użyciu przeciążone nierówności (`!=`) operatora, a na końcu <xref:System.Windows.Media.Media3D.Point3D> struktury i <xref:System.Windows.Media.Media3D.Point4D> Struktura są sprawdzane pod kątem równości przy użyciu statycznych <xref:System.Windows.Media.Media3D.Point4D.Equals%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c49a3-105">The <xref:System.Windows.Media.Media3D.Point4D> structures are tested for equality using the overloaded equality (`==`) operator, then for inequality using the overloaded inequality (`!=`) operator, and finally a <xref:System.Windows.Media.Media3D.Point3D> structure and a <xref:System.Windows.Media.Media3D.Point4D> structure are checked for equality using the static <xref:System.Windows.Media.Media3D.Point4D.Equals%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c49a3-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="c49a3-106">Example</span></span>  
 [!code-csharp[3DGallery_procedural_snip#Point4DEqualityExample_csharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Misc3DOperationsExample.cs#point4dequalityexample_csharp)]  
  
## <a name="see-also"></a><span data-ttu-id="c49a3-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c49a3-107">See Also</span></span>  
 <xref:System.Windows.Media.Media3D.Point4D.op_Equality%2A>  
 <xref:System.Windows.Media.Media3D.Point4D.op_Inequality%2A>  
 <xref:System.Windows.Media.Media3D.Point4D.Equals%2A>
