---
title: Omówienie grafik
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
ms.openlocfilehash: f0e2fd9dcf31e5fdce16b5a3b6fd21eab6eab66a
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505322"
---
# <a name="overview-of-graphics"></a><span data-ttu-id="b9780-102">Omówienie grafik</span><span class="sxs-lookup"><span data-stu-id="b9780-102">Overview of Graphics</span></span>
<span data-ttu-id="b9780-103">GDI + jest interfejs programowania aplikacji (API), który wchodzi w skład podsystemu systemu operacyjnego Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="b9780-103">GDI+ is an application programming interface (API) that forms the subsystem of the Microsoft Windows operating system.</span></span> <span data-ttu-id="b9780-104">GDI + jest odpowiedzialny za wyświetlanie informacji na ekranach i drukarki.</span><span class="sxs-lookup"><span data-stu-id="b9780-104">GDI+ is responsible for displaying information on screens and printers.</span></span> <span data-ttu-id="b9780-105">Jak sugeruje nazwa, GDI + jest następcą programu interfejsu GDI, graficzny interfejs urządzenia dołączone do wcześniejszych wersji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b9780-105">As its name suggests, GDI+ is the successor to GDI, the Graphics Device Interface included with earlier versions of Windows.</span></span>  
  
## <a name="managed-class-interface"></a><span data-ttu-id="b9780-106">Interfejs klasy zarządzanej</span><span class="sxs-lookup"><span data-stu-id="b9780-106">Managed Class Interface</span></span>  
 <span data-ttu-id="b9780-107">Interfejs API GDI + jest udostępniany za pośrednictwem zestaw klas wdrożone jako kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="b9780-107">The GDI+ API is exposed through a set of classes deployed as managed code.</span></span> <span data-ttu-id="b9780-108">Ten zestaw klas jest nazywany *interfejsu klasy zarządzanej* do interfejsu GDI +.</span><span class="sxs-lookup"><span data-stu-id="b9780-108">This set of classes is called the *managed class interface* to GDI+.</span></span> <span data-ttu-id="b9780-109">Następujące przestrzenie nazw tworzą interfejs zarządzanej klasy:</span><span class="sxs-lookup"><span data-stu-id="b9780-109">The following namespaces make up the managed class interface:</span></span>  
  
- <xref:System.Drawing>  
  
- <xref:System.Drawing.Drawing2D>  
  
- <xref:System.Drawing.Imaging>  
  
- <xref:System.Drawing.Text>  
  
- <xref:System.Drawing.Printing>  
  
 <span data-ttu-id="b9780-110">Za pomocą graficzny interfejs urządzenia, takich jak interfejs GDI + można wyświetlić informacje na ekranie lub drukarki, bez konieczności liczyć się szczegółowe informacje o urządzeniu określonej.</span><span class="sxs-lookup"><span data-stu-id="b9780-110">With a Graphics Device Interface, such as GDI+, you can display information on a screen or printer without having to be concerned about the details of a particular display device.</span></span> <span data-ttu-id="b9780-111">Programistę wykonywania wywołań do metod dostarczonych przez klasy interfejsu GDI +.</span><span class="sxs-lookup"><span data-stu-id="b9780-111">The programmer makes calls to methods provided by GDI+ classes.</span></span> <span data-ttu-id="b9780-112">Tych metod należy z kolei odpowiednie wywołania określone sterowniki urządzeń.</span><span class="sxs-lookup"><span data-stu-id="b9780-112">Those methods, in turn, make the appropriate calls to specific device drivers.</span></span> <span data-ttu-id="b9780-113">GDI + powoduje, że aplikacja od sprzętu graficznego.</span><span class="sxs-lookup"><span data-stu-id="b9780-113">GDI+ insulates the application from the graphics hardware.</span></span> <span data-ttu-id="b9780-114">Jest to izolacji, umożliwiająca z programistą podczas tworzenia aplikacji niezależnych od urządzenia.</span><span class="sxs-lookup"><span data-stu-id="b9780-114">It is this insulation that enables a programmer to create device-independent applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9780-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9780-115">See also</span></span>

- [<span data-ttu-id="b9780-116">Grafika — omówienie</span><span class="sxs-lookup"><span data-stu-id="b9780-116">Graphics Overview</span></span>](graphics-overview-windows-forms.md)
