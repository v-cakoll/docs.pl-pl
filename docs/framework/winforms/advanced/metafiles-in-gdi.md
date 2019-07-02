---
title: Metapliki w GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], metafiles
- GDI+, metafiles
- metafiles
ms.assetid: 51da872c-c783-440f-8bf6-1e580a966c31
ms.openlocfilehash: df54289722cf12bad840722c6eafdaa43279a5dc
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504583"
---
# <a name="metafiles-in-gdi"></a><span data-ttu-id="eb1d1-102">Metapliki w GDI+</span><span class="sxs-lookup"><span data-stu-id="eb1d1-102">Metafiles in GDI+</span></span>
<span data-ttu-id="eb1d1-103">GDI + zapewnia <xref:System.Drawing.Imaging.Metafile> klasy, dzięki czemu mogą rejestrować i wyświetlanie metaplików.</span><span class="sxs-lookup"><span data-stu-id="eb1d1-103">GDI+ provides the <xref:System.Drawing.Imaging.Metafile> class so that you can record and display metafiles.</span></span> <span data-ttu-id="eb1d1-104">Metaplik, nazywany również obrazem wektora jest obraz, który jest przechowywany jako sekwencja rysowania poleceń i ustawień.</span><span class="sxs-lookup"><span data-stu-id="eb1d1-104">A metafile, also called a vector image, is an image that is stored as a sequence of drawing commands and settings.</span></span> <span data-ttu-id="eb1d1-105">Polecenia i ustawienia są rejestrowane w <xref:System.Drawing.Imaging.Metafile> obiektu, które mogą być przechowywane w pamięci lub zapisany do pliku lub strumienia.</span><span class="sxs-lookup"><span data-stu-id="eb1d1-105">The commands and settings recorded in a <xref:System.Drawing.Imaging.Metafile> object can be stored in memory or saved to a file or stream.</span></span>  
  
## <a name="metafile-formats"></a><span data-ttu-id="eb1d1-106">Formaty metaplików</span><span class="sxs-lookup"><span data-stu-id="eb1d1-106">Metafile Formats</span></span>  
 <span data-ttu-id="eb1d1-107">GDI + można wyświetlić metapliki, które były przechowywane w następujących formatach:</span><span class="sxs-lookup"><span data-stu-id="eb1d1-107">GDI+ can display metafiles that have been stored in the following formats:</span></span>  
  
- <span data-ttu-id="eb1d1-108">Windows metaplików (WMF)</span><span class="sxs-lookup"><span data-stu-id="eb1d1-108">Windows Metafile (WMF)</span></span>  
  
- <span data-ttu-id="eb1d1-109">Rozszerzony metaplik (EMF)</span><span class="sxs-lookup"><span data-stu-id="eb1d1-109">Enhanced Metafile (EMF)</span></span>  
  
- <span data-ttu-id="eb1d1-110">EMF+</span><span class="sxs-lookup"><span data-stu-id="eb1d1-110">EMF+</span></span>  
  
 <span data-ttu-id="eb1d1-111">GDI + można rejestrować metapliki format EMF i EMF +, ale nie w formacie programu WMF.</span><span class="sxs-lookup"><span data-stu-id="eb1d1-111">GDI+ can record metafiles in the EMF and EMF+ formats, but not in the WMF format.</span></span>  
  
 <span data-ttu-id="eb1d1-112">EMF + jest rozszerzeniem EMF umożliwiająca GDI + rekordy mają być przechowywane.</span><span class="sxs-lookup"><span data-stu-id="eb1d1-112">EMF+ is an extension to EMF that allows GDI+ records to be stored.</span></span> <span data-ttu-id="eb1d1-113">Istnieją dwie odmiany format EMF +: EMF + tylko i EMF + dwa porty.</span><span class="sxs-lookup"><span data-stu-id="eb1d1-113">There are two variations on the EMF+ format: EMF+ Only and EMF+ Dual.</span></span> <span data-ttu-id="eb1d1-114">Metapliki EMF + tylko zawierać tylko rekordy GDI +.</span><span class="sxs-lookup"><span data-stu-id="eb1d1-114">EMF+ Only metafiles contain only GDI+ records.</span></span> <span data-ttu-id="eb1d1-115">Metapliki takie mogą być wyświetlane w GDI +, ale nie GDI.</span><span class="sxs-lookup"><span data-stu-id="eb1d1-115">Such metafiles can be displayed by GDI+ but not by GDI.</span></span> <span data-ttu-id="eb1d1-116">Metapliki EMF + podwójnego zawiera rekordy GDI + i GDI.</span><span class="sxs-lookup"><span data-stu-id="eb1d1-116">EMF+ Dual metafiles contain GDI+ and GDI records.</span></span> <span data-ttu-id="eb1d1-117">Każdy rekord GDI + w metaplik EMF + podwójnego jest powiązany z alternatywny rekord GDI.</span><span class="sxs-lookup"><span data-stu-id="eb1d1-117">Each GDI+ record in an EMF+ Dual metafile is paired with an alternate GDI record.</span></span> <span data-ttu-id="eb1d1-118">Metapliki takie mogą być wyświetlane w GDI + lub GDI.</span><span class="sxs-lookup"><span data-stu-id="eb1d1-118">Such metafiles can be displayed by GDI+ or by GDI.</span></span>  
  
 <span data-ttu-id="eb1d1-119">Poniższy przykład wyświetla metaplik, który został wcześniej zapisany jako plik.</span><span class="sxs-lookup"><span data-stu-id="eb1d1-119">The following example displays a metafile that was previously saved as a file.</span></span> <span data-ttu-id="eb1d1-120">Metaplik jest wyświetlany z jego lewego górnego rogu w (100, 100).</span><span class="sxs-lookup"><span data-stu-id="eb1d1-120">The metafile is displayed with its upper-left corner at (100, 100).</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="eb1d1-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eb1d1-121">See also</span></span>

- [<span data-ttu-id="eb1d1-122">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="eb1d1-122">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
