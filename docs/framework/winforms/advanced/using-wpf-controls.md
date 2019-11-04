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
# <a name="use-wpf-controls-in-windows-forms-apps"></a>Korzystanie z formantów WPF w aplikacjach Windows Forms

W aplikacjach opartych na Windows Forms można używać formantów Windows Presentation Foundation (WPF). Chociaż są to dwie różne technologie wyświetlania, działają bezproblemowo.

Projektant formularzy systemu Windows w programie Visual Studio udostępnia środowisko projektowania wizualnego do hostowania formantów Windows Presentation Foundation. Kontrolka WPF jest hostowana przez specjalną kontrolkę Windows Forms o nazwie <xref:System.Windows.Forms.Integration.ElementHost>. Ta kontrolka umożliwia uczestnictwo formantu WPF w układzie formularza oraz odbieranie komunikatów z klawiatury i myszy. W czasie projektowania można rozmieścić kontrolkę <xref:System.Windows.Forms.Integration.ElementHost> tak samo jak każda kontrolka Windows Forms.

Można również użyć formantów Windows Forms w aplikacjach opartych na platformie WPF. Aby uzyskać więcej informacji, zobacz [Designing XAML in Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).

## <a name="see-also"></a>Zobacz także

- [WPF i Windows Forms międzyoperacyjności](../../wpf/advanced/wpf-and-windows-forms-interoperation.md)
