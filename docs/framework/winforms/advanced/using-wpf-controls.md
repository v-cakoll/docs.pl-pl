---
title: Korzystanie z formantów WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9883e9d31fc9e3e2ec3ca06b4fc830bcdc338ae
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460694"
---
# <a name="use-wpf-controls-in-windows-forms-apps"></a><span data-ttu-id="5e1c6-102">Korzystanie z formantów WPF w aplikacjach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5e1c6-102">Use WPF controls in Windows Forms apps</span></span>

<span data-ttu-id="5e1c6-103">W aplikacjach opartych na Windows Forms można używać formantów Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="5e1c6-103">You can use Windows Presentation Foundation (WPF) controls in Windows Forms-based applications.</span></span> <span data-ttu-id="5e1c6-104">Chociaż są to dwie różne technologie wyświetlania, działają bezproblemowo.</span><span class="sxs-lookup"><span data-stu-id="5e1c6-104">Although these are two different view technologies, they interoperate smoothly.</span></span>

<span data-ttu-id="5e1c6-105">Projektant formularzy systemu Windows w programie Visual Studio udostępnia środowisko projektowania wizualnego do hostowania formantów Windows Presentation Foundation.</span><span class="sxs-lookup"><span data-stu-id="5e1c6-105">The Windows Forms Designer in Visual Studio provides a visual design environment for hosting Windows Presentation Foundation controls.</span></span> <span data-ttu-id="5e1c6-106">Kontrolka WPF jest hostowana przez specjalną kontrolkę Windows Forms o nazwie <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="5e1c6-106">A WPF control is hosted by a special Windows Forms control that's named <xref:System.Windows.Forms.Integration.ElementHost>.</span></span> <span data-ttu-id="5e1c6-107">Ta kontrolka umożliwia uczestnictwo formantu WPF w układzie formularza oraz odbieranie komunikatów z klawiatury i myszy.</span><span class="sxs-lookup"><span data-stu-id="5e1c6-107">This control enables the WPF control to participate in the form's layout and to receive keyboard and mouse messages.</span></span> <span data-ttu-id="5e1c6-108">W czasie projektowania można rozmieścić kontrolkę <xref:System.Windows.Forms.Integration.ElementHost> tak samo jak każda kontrolka Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5e1c6-108">At design time, you can arrange the <xref:System.Windows.Forms.Integration.ElementHost> control just as you would any Windows Forms control.</span></span>

<span data-ttu-id="5e1c6-109">Można również użyć formantów Windows Forms w aplikacjach opartych na platformie WPF.</span><span class="sxs-lookup"><span data-stu-id="5e1c6-109">You can also use Windows Forms controls in WPF-based applications.</span></span> <span data-ttu-id="5e1c6-110">Aby uzyskać więcej informacji, zobacz [Designing XAML in Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="5e1c6-110">For more information, see [Design XAML in Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).</span></span>

## <a name="see-also"></a><span data-ttu-id="5e1c6-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e1c6-111">See also</span></span>

- [<span data-ttu-id="5e1c6-112">WPF i Windows Forms międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="5e1c6-112">WPF and Windows Forms interoperation</span></span>](../../wpf/advanced/wpf-and-windows-forms-interoperation.md)
