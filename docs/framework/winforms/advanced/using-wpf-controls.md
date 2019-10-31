---
title: Korzystanie z formantów WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5e05ec7fc503565333a4d05662a4e40d8d1193af
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197462"
---
# <a name="use-wpf-controls-in-windows-forms-apps"></a><span data-ttu-id="f28f7-102">Korzystanie z formantów WPF w aplikacjach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f28f7-102">Use WPF controls in Windows Forms apps</span></span>

<span data-ttu-id="f28f7-103">W aplikacjach opartych na Windows Forms można używać formantów Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="f28f7-103">You can use Windows Presentation Foundation (WPF) controls in Windows Forms-based applications.</span></span> <span data-ttu-id="f28f7-104">Chociaż są to dwie różne technologie wyświetlania, działają bezproblemowo.</span><span class="sxs-lookup"><span data-stu-id="f28f7-104">Although these are two different view technologies, they interoperate smoothly.</span></span>

<span data-ttu-id="f28f7-105">Projektant formularzy systemu Windows w programie Visual Studio udostępnia środowisko projektowania wizualnego do hostowania formantów Windows Presentation Foundation.</span><span class="sxs-lookup"><span data-stu-id="f28f7-105">The Windows Forms Designer in Visual Studio provides a visual design environment for hosting Windows Presentation Foundation controls.</span></span> <span data-ttu-id="f28f7-106">Kontrolka WPF jest hostowana przez specjalną kontrolkę Windows Forms o nazwie <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="f28f7-106">A WPF control is hosted by a special Windows Forms control that's named <xref:System.Windows.Forms.Integration.ElementHost>.</span></span> <span data-ttu-id="f28f7-107">Ta kontrolka umożliwia uczestnictwo formantu WPF w układzie formularza oraz odbieranie komunikatów z klawiatury i myszy.</span><span class="sxs-lookup"><span data-stu-id="f28f7-107">This control enables the WPF control to participate in the form's layout and to receive keyboard and mouse messages.</span></span> <span data-ttu-id="f28f7-108">W czasie projektowania można rozmieścić kontrolkę <xref:System.Windows.Forms.Integration.ElementHost> tak samo jak każda kontrolka Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f28f7-108">At design time, you can arrange the <xref:System.Windows.Forms.Integration.ElementHost> control just as you would any Windows Forms control.</span></span>

<span data-ttu-id="f28f7-109">Można również użyć formantów Windows Forms w aplikacjach opartych na platformie WPF.</span><span class="sxs-lookup"><span data-stu-id="f28f7-109">You can also use Windows Forms controls in WPF-based applications.</span></span> <span data-ttu-id="f28f7-110">Aby uzyskać więcej informacji, zobacz [Designing XAML in Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="f28f7-110">For more information, see [Design XAML in Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).</span></span>

## <a name="see-also"></a><span data-ttu-id="f28f7-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f28f7-111">See also</span></span>

- [<span data-ttu-id="f28f7-112">WPF i Windows Forms międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="f28f7-112">WPF and Windows Forms interoperation</span></span>](../../wpf/advanced/wpf-and-windows-forms-interoperation.md)
