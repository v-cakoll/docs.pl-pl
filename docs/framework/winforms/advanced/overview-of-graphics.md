---
title: Omówienie grafik
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
ms.openlocfilehash: a69bfc2e9983484f90b1b65abd234df2519b503e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523556"
---
# <a name="overview-of-graphics"></a><span data-ttu-id="4bb5a-102">Omówienie grafik</span><span class="sxs-lookup"><span data-stu-id="4bb5a-102">Overview of Graphics</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="4bb5a-103"> to interfejs programowania aplikacji (API), który wchodzi w skład podsystemu systemu operacyjnego Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="4bb5a-103"> is an application programming interface (API) that forms the subsystem of the Microsoft Windows operating system.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="4bb5a-104"> odpowiada za wyświetlanie informacji na ekranach i drukarek.</span><span class="sxs-lookup"><span data-stu-id="4bb5a-104"> is responsible for displaying information on screens and printers.</span></span> <span data-ttu-id="4bb5a-105">Zgodnie z sugestią, jego nazwa, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] zastępuje [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], graficzny interfejs urządzenia dołączone do wcześniejszych wersji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="4bb5a-105">As its name suggests, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] is the successor to [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], the Graphics Device Interface included with earlier versions of Windows.</span></span>  
  
## <a name="managed-class-interface"></a><span data-ttu-id="4bb5a-106">Zarządzanej klasy interfejsu</span><span class="sxs-lookup"><span data-stu-id="4bb5a-106">Managed Class Interface</span></span>  
 <span data-ttu-id="4bb5a-107">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Interfejsu API jest za pośrednictwem zestaw klas wdrożony jako kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="4bb5a-107">The [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] API is exposed through a set of classes deployed as managed code.</span></span> <span data-ttu-id="4bb5a-108">Ten zestaw klas jest nazywany *zarządzanej klasy interfejsu* do [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4bb5a-108">This set of classes is called the *managed class interface* to [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span> <span data-ttu-id="4bb5a-109">Następujące obszary nazw tworzą interfejsu zarządzanej klasy:</span><span class="sxs-lookup"><span data-stu-id="4bb5a-109">The following namespaces make up the managed class interface:</span></span>  
  
-   <xref:System.Drawing>  
  
-   <xref:System.Drawing.Drawing2D>  
  
-   <xref:System.Drawing.Imaging>  
  
-   <xref:System.Drawing.Text>  
  
-   <xref:System.Drawing.Printing>  
  
 <span data-ttu-id="4bb5a-110">Z graficzny interfejs urządzenia takie jak [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], można wyświetlić informacje dotyczące ekranu lub drukarki, bez konieczności trzeba się troszczyć o szczegóły określony ekran urządzenia.</span><span class="sxs-lookup"><span data-stu-id="4bb5a-110">With a Graphics Device Interface, such as [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can display information on a screen or printer without having to be concerned about the details of a particular display device.</span></span> <span data-ttu-id="4bb5a-111">Programistę wykonywania wywołań do metod dostarczonych przez [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] klasy.</span><span class="sxs-lookup"><span data-stu-id="4bb5a-111">The programmer makes calls to methods provided by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes.</span></span> <span data-ttu-id="4bb5a-112">Tych metod z kolei wywołań odpowiednie do określone sterowniki urządzeń.</span><span class="sxs-lookup"><span data-stu-id="4bb5a-112">Those methods, in turn, make the appropriate calls to specific device drivers.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="4bb5a-113"> powoduje aplikacji od sprzętu grafiki.</span><span class="sxs-lookup"><span data-stu-id="4bb5a-113"> insulates the application from the graphics hardware.</span></span> <span data-ttu-id="4bb5a-114">Jest izolacja umożliwiającą programisty do tworzenia aplikacji niezależnych od urządzenia.</span><span class="sxs-lookup"><span data-stu-id="4bb5a-114">It is this insulation that enables a programmer to create device-independent applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bb5a-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4bb5a-115">See Also</span></span>  
 [<span data-ttu-id="4bb5a-116">Grafika — omówienie</span><span class="sxs-lookup"><span data-stu-id="4bb5a-116">Graphics Overview</span></span>](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)
