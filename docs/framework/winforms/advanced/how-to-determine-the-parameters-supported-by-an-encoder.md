---
title: 'Instrukcje: Określanie parametrów obsługiwanych przez koder'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encoder parameters [Windows Forms], determining supported
ms.assetid: f47ae459-e3ce-4d41-a140-2f6c6aea3f44
ms.openlocfilehash: 3e5345180e0ff3321b9ef0b885b836d3e9456f28
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64643337"
---
# <a name="how-to-determine-the-parameters-supported-by-an-encoder"></a><span data-ttu-id="40f0c-102">Instrukcje: Określanie parametrów obsługiwanych przez koder</span><span class="sxs-lookup"><span data-stu-id="40f0c-102">How to: Determine the Parameters Supported by an Encoder</span></span>
<span data-ttu-id="40f0c-103">Można dostosować parametry obrazu, takie jak poziom jakości i kompresji, ale musisz wiedzieć, które parametry są obsługiwane przez koder danego obrazu.</span><span class="sxs-lookup"><span data-stu-id="40f0c-103">You can adjust image parameters, such as quality and compression level, but you must know which parameters are supported by a given image encoder.</span></span> <span data-ttu-id="40f0c-104"><xref:System.Drawing.Image> Klasa udostępnia <xref:System.Drawing.Image.GetEncoderParameterList%2A> metody, dzięki czemu można określić parametry obrazu, które są obsługiwane w przypadku określonego kodera.</span><span class="sxs-lookup"><span data-stu-id="40f0c-104">The <xref:System.Drawing.Image> class provides the <xref:System.Drawing.Image.GetEncoderParameterList%2A> method so that you can determine which image parameters are supported for a particular encoder.</span></span> <span data-ttu-id="40f0c-105">Należy określić kodera z identyfikatorem GUID.</span><span class="sxs-lookup"><span data-stu-id="40f0c-105">You specify the encoder with a GUID.</span></span> <span data-ttu-id="40f0c-106"><xref:System.Drawing.Image.GetEncoderParameterList%2A> Metoda zwraca tablicę <xref:System.Drawing.Imaging.EncoderParameter> obiektów.</span><span class="sxs-lookup"><span data-stu-id="40f0c-106">The <xref:System.Drawing.Image.GetEncoderParameterList%2A> method returns an array of <xref:System.Drawing.Imaging.EncoderParameter> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40f0c-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="40f0c-107">Example</span></span>  
 <span data-ttu-id="40f0c-108">Poniższy przykład kodu wyświetla obsługiwanych parametrów dla kodera JPEG.</span><span class="sxs-lookup"><span data-stu-id="40f0c-108">The following example code outputs the supported parameters for the JPEG encoder.</span></span> <span data-ttu-id="40f0c-109">Użyj listy parametrów kategorii i skojarzone identyfikatory GUID <xref:System.Drawing.Imaging.Encoder> Przegląd klasy w celu ustalenia kategorii każdego parametru.</span><span class="sxs-lookup"><span data-stu-id="40f0c-109">Use the list of parameter categories and associated GUIDs in the <xref:System.Drawing.Imaging.Encoder> class overview to determine the category for each parameter.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#3](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#3)]
 [!code-vb[UsingImageEncodersDecoders#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="40f0c-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="40f0c-110">Compiling the Code</span></span>  
 <span data-ttu-id="40f0c-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="40f0c-111">This example requires:</span></span>  
  
- <span data-ttu-id="40f0c-112">Aplikacja Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="40f0c-112">A Windows Forms application.</span></span>  
  
- <span data-ttu-id="40f0c-113">A <xref:System.Windows.Forms.PaintEventArgs>, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="40f0c-113">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40f0c-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40f0c-114">See also</span></span>

- [<span data-ttu-id="40f0c-115">Instrukcje: Lista zainstalowanych koderów</span><span class="sxs-lookup"><span data-stu-id="40f0c-115">How to: List Installed Encoders</span></span>](how-to-list-installed-encoders.md)
- [<span data-ttu-id="40f0c-116">Typy map bitowych</span><span class="sxs-lookup"><span data-stu-id="40f0c-116">Types of Bitmaps</span></span>](types-of-bitmaps.md)
- [<span data-ttu-id="40f0c-117">Używanie kodeków obrazu w zarządzanym GDI+</span><span class="sxs-lookup"><span data-stu-id="40f0c-117">Using Image Encoders and Decoders in Managed GDI+</span></span>](using-image-encoders-and-decoders-in-managed-gdi.md)
