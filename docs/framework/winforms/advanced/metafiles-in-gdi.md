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
ms.openlocfilehash: f46c24b699aa49db2bc4b8467ce96a125602acec
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645747"
---
# <a name="metafiles-in-gdi"></a><span data-ttu-id="6989c-102">Metapliki w GDI+</span><span class="sxs-lookup"><span data-stu-id="6989c-102">Metafiles in GDI+</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="6989c-103">udostępnia <xref:System.Drawing.Imaging.Metafile> klasy, dzięki czemu mogą rejestrować i wyświetlanie metaplików.</span><span class="sxs-lookup"><span data-stu-id="6989c-103">provides the <xref:System.Drawing.Imaging.Metafile> class so that you can record and display metafiles.</span></span> <span data-ttu-id="6989c-104">Metaplik, nazywany również obrazem wektora jest obraz, który jest przechowywany jako sekwencja rysowania poleceń i ustawień.</span><span class="sxs-lookup"><span data-stu-id="6989c-104">A metafile, also called a vector image, is an image that is stored as a sequence of drawing commands and settings.</span></span> <span data-ttu-id="6989c-105">Polecenia i ustawienia są rejestrowane w <xref:System.Drawing.Imaging.Metafile> obiektu, które mogą być przechowywane w pamięci lub zapisany do pliku lub strumienia.</span><span class="sxs-lookup"><span data-stu-id="6989c-105">The commands and settings recorded in a <xref:System.Drawing.Imaging.Metafile> object can be stored in memory or saved to a file or stream.</span></span>  
  
## <a name="metafile-formats"></a><span data-ttu-id="6989c-106">Formaty metaplików</span><span class="sxs-lookup"><span data-stu-id="6989c-106">Metafile Formats</span></span>  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="6989c-107">można wyświetlić metapliki, które były przechowywane w następujących formatach:</span><span class="sxs-lookup"><span data-stu-id="6989c-107">can display metafiles that have been stored in the following formats:</span></span>  
  
- <span data-ttu-id="6989c-108">Windows metaplików (WMF)</span><span class="sxs-lookup"><span data-stu-id="6989c-108">Windows Metafile (WMF)</span></span>  
  
- <span data-ttu-id="6989c-109">Rozszerzony metaplik (EMF)</span><span class="sxs-lookup"><span data-stu-id="6989c-109">Enhanced Metafile (EMF)</span></span>  
  
- <span data-ttu-id="6989c-110">EMF+</span><span class="sxs-lookup"><span data-stu-id="6989c-110">EMF+</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="6989c-111">można rejestrować metapliki format EMF i EMF +, ale nie w formacie programu WMF.</span><span class="sxs-lookup"><span data-stu-id="6989c-111">can record metafiles in the EMF and EMF+ formats, but not in the WMF format.</span></span>  
  
 <span data-ttu-id="6989c-112">EMF + jest rozszerzeniem EMF, która umożliwia [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] rekordy, które mają być przechowywane.</span><span class="sxs-lookup"><span data-stu-id="6989c-112">EMF+ is an extension to EMF that allows [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] records to be stored.</span></span> <span data-ttu-id="6989c-113">Istnieją dwie odmiany format EMF +: EMF + tylko i EMF + dwa porty.</span><span class="sxs-lookup"><span data-stu-id="6989c-113">There are two variations on the EMF+ format: EMF+ Only and EMF+ Dual.</span></span> <span data-ttu-id="6989c-114">Metapliki EMF + tylko zawierają tylko [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] rekordów.</span><span class="sxs-lookup"><span data-stu-id="6989c-114">EMF+ Only metafiles contain only [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] records.</span></span> <span data-ttu-id="6989c-115">Metapliki takie mogą być wyświetlane przez [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] , ale nie za [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6989c-115">Such metafiles can be displayed by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] but not by [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span> <span data-ttu-id="6989c-116">Metapliki EMF + podwójne zawiera [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] i [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] rekordów.</span><span class="sxs-lookup"><span data-stu-id="6989c-116">EMF+ Dual metafiles contain [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] records.</span></span> <span data-ttu-id="6989c-117">Każdy [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] rekordów w podwójne EMF + metaplik jest powiązany z alternatywnego [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] rekordu.</span><span class="sxs-lookup"><span data-stu-id="6989c-117">Each [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] record in an EMF+ Dual metafile is paired with an alternate [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] record.</span></span> <span data-ttu-id="6989c-118">Metapliki takie mogą być wyświetlane przez [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] lub [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6989c-118">Such metafiles can be displayed by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] or by [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 <span data-ttu-id="6989c-119">Poniższy przykład wyświetla metaplik, który został wcześniej zapisany jako plik.</span><span class="sxs-lookup"><span data-stu-id="6989c-119">The following example displays a metafile that was previously saved as a file.</span></span> <span data-ttu-id="6989c-120">Metaplik jest wyświetlany z jego lewego górnego rogu w (100, 100).</span><span class="sxs-lookup"><span data-stu-id="6989c-120">The metafile is displayed with its upper-left corner at (100, 100).</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="6989c-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6989c-121">See also</span></span>

- [<span data-ttu-id="6989c-122">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="6989c-122">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
