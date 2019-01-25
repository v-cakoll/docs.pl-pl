---
title: Omówienie grafik
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
ms.openlocfilehash: c569eb249a583ca9f71381210eeb11a8d10b04e5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590204"
---
# <a name="overview-of-graphics"></a><span data-ttu-id="8a868-102">Omówienie grafik</span><span class="sxs-lookup"><span data-stu-id="8a868-102">Overview of Graphics</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="8a868-103">to interfejs programowania aplikacji (API), który wchodzi w skład podsystemu systemu operacyjnego Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="8a868-103">is an application programming interface (API) that forms the subsystem of the Microsoft Windows operating system.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="8a868-104">odpowiada za wyświetlanie informacji na ekranach i drukarki.</span><span class="sxs-lookup"><span data-stu-id="8a868-104">is responsible for displaying information on screens and printers.</span></span> <span data-ttu-id="8a868-105">Jak sugeruje nazwa, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] jest następcą programu [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], graficzny interfejs urządzenia dołączone do wcześniejszych wersji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8a868-105">As its name suggests, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] is the successor to [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], the Graphics Device Interface included with earlier versions of Windows.</span></span>  
  
## <a name="managed-class-interface"></a><span data-ttu-id="8a868-106">Interfejs klasy zarządzanej</span><span class="sxs-lookup"><span data-stu-id="8a868-106">Managed Class Interface</span></span>  
 <span data-ttu-id="8a868-107">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Interfejs API jest udostępniany za pośrednictwem zestaw klas wdrożone jako kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="8a868-107">The [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] API is exposed through a set of classes deployed as managed code.</span></span> <span data-ttu-id="8a868-108">Ten zestaw klas jest nazywany *interfejsu klasy zarządzanej* do [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8a868-108">This set of classes is called the *managed class interface* to [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span> <span data-ttu-id="8a868-109">Następujące przestrzenie nazw tworzą interfejs zarządzanej klasy:</span><span class="sxs-lookup"><span data-stu-id="8a868-109">The following namespaces make up the managed class interface:</span></span>  
  
-   <xref:System.Drawing>  
  
-   <xref:System.Drawing.Drawing2D>  
  
-   <xref:System.Drawing.Imaging>  
  
-   <xref:System.Drawing.Text>  
  
-   <xref:System.Drawing.Printing>  
  
 <span data-ttu-id="8a868-110">Za pomocą graficzny interfejs urządzenia takie jak [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], informacje możesz wyświetlać na ekranie lub drukarki, bez konieczności liczyć się szczegółowe informacje o urządzeniu określony ekran.</span><span class="sxs-lookup"><span data-stu-id="8a868-110">With a Graphics Device Interface, such as [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can display information on a screen or printer without having to be concerned about the details of a particular display device.</span></span> <span data-ttu-id="8a868-111">Programistę wykonywania wywołań do metod dostarczonych przez [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] klasy.</span><span class="sxs-lookup"><span data-stu-id="8a868-111">The programmer makes calls to methods provided by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes.</span></span> <span data-ttu-id="8a868-112">Tych metod należy z kolei odpowiednie wywołania określone sterowniki urządzeń.</span><span class="sxs-lookup"><span data-stu-id="8a868-112">Those methods, in turn, make the appropriate calls to specific device drivers.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="8a868-113">powoduje, że aplikacja od sprzętu graficznego.</span><span class="sxs-lookup"><span data-stu-id="8a868-113">insulates the application from the graphics hardware.</span></span> <span data-ttu-id="8a868-114">Jest to izolacji, umożliwiająca z programistą podczas tworzenia aplikacji niezależnych od urządzenia.</span><span class="sxs-lookup"><span data-stu-id="8a868-114">It is this insulation that enables a programmer to create device-independent applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a868-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a868-115">See also</span></span>
- [<span data-ttu-id="8a868-116">Grafika — omówienie</span><span class="sxs-lookup"><span data-stu-id="8a868-116">Graphics Overview</span></span>](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)
