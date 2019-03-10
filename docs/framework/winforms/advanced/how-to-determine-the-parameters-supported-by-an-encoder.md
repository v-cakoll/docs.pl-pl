---
title: 'Instrukcje: Określanie parametrów obsługiwanych przez koder'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encoder parameters [Windows Forms], determining supported
ms.assetid: f47ae459-e3ce-4d41-a140-2f6c6aea3f44
ms.openlocfilehash: f5af00833c8d8373444b475673709d902598d9d0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57719705"
---
# <a name="how-to-determine-the-parameters-supported-by-an-encoder"></a><span data-ttu-id="b65c4-102">Instrukcje: Określanie parametrów obsługiwanych przez koder</span><span class="sxs-lookup"><span data-stu-id="b65c4-102">How to: Determine the Parameters Supported by an Encoder</span></span>
<span data-ttu-id="b65c4-103">Można dostosować parametry obrazu, takie jak poziom jakości i kompresji, ale musisz wiedzieć, które parametry są obsługiwane przez koder danego obrazu.</span><span class="sxs-lookup"><span data-stu-id="b65c4-103">You can adjust image parameters, such as quality and compression level, but you must know which parameters are supported by a given image encoder.</span></span> <span data-ttu-id="b65c4-104"><xref:System.Drawing.Image> Klasa udostępnia <xref:System.Drawing.Image.GetEncoderParameterList%2A> metody, dzięki czemu można określić parametry obrazu, które są obsługiwane w przypadku określonego kodera.</span><span class="sxs-lookup"><span data-stu-id="b65c4-104">The <xref:System.Drawing.Image> class provides the <xref:System.Drawing.Image.GetEncoderParameterList%2A> method so that you can determine which image parameters are supported for a particular encoder.</span></span> <span data-ttu-id="b65c4-105">Należy określić kodera z identyfikatorem GUID.</span><span class="sxs-lookup"><span data-stu-id="b65c4-105">You specify the encoder with a GUID.</span></span> <span data-ttu-id="b65c4-106"><xref:System.Drawing.Image.GetEncoderParameterList%2A> Metoda zwraca tablicę <xref:System.Drawing.Imaging.EncoderParameter> obiektów.</span><span class="sxs-lookup"><span data-stu-id="b65c4-106">The <xref:System.Drawing.Image.GetEncoderParameterList%2A> method returns an array of <xref:System.Drawing.Imaging.EncoderParameter> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b65c4-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="b65c4-107">Example</span></span>  
 <span data-ttu-id="b65c4-108">Poniższy przykład kodu wyświetla obsługiwanych parametrów dla kodera JPEG.</span><span class="sxs-lookup"><span data-stu-id="b65c4-108">The following example code outputs the supported parameters for the JPEG encoder.</span></span> <span data-ttu-id="b65c4-109">Użyj listy parametrów kategorii i skojarzone identyfikatory GUID <xref:System.Drawing.Imaging.Encoder> Przegląd klasy w celu ustalenia kategorii każdego parametru.</span><span class="sxs-lookup"><span data-stu-id="b65c4-109">Use the list of parameter categories and associated GUIDs in the <xref:System.Drawing.Imaging.Encoder> class overview to determine the category for each parameter.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#3](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#3)]
 [!code-vb[UsingImageEncodersDecoders#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b65c4-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b65c4-110">Compiling the Code</span></span>  
 <span data-ttu-id="b65c4-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="b65c4-111">This example requires:</span></span>  
  
-   <span data-ttu-id="b65c4-112">Aplikacja Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b65c4-112">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="b65c4-113">A <xref:System.Windows.Forms.PaintEventArgs>, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="b65c4-113">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b65c4-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b65c4-114">See also</span></span>
- [<span data-ttu-id="b65c4-115">Instrukcje: Lista zainstalowanych koderów</span><span class="sxs-lookup"><span data-stu-id="b65c4-115">How to: List Installed Encoders</span></span>](how-to-list-installed-encoders.md)
- [<span data-ttu-id="b65c4-116">Typy map bitowych</span><span class="sxs-lookup"><span data-stu-id="b65c4-116">Types of Bitmaps</span></span>](types-of-bitmaps.md)
- [<span data-ttu-id="b65c4-117">Używanie kodeków obrazu w zarządzanym GDI+</span><span class="sxs-lookup"><span data-stu-id="b65c4-117">Using Image Encoders and Decoders in Managed GDI+</span></span>](using-image-encoders-and-decoders-in-managed-gdi.md)
