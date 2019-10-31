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
# <a name="use-wpf-controls-in-windows-forms-apps"></a>Korzystanie z formantów WPF w aplikacjach Windows Forms

W aplikacjach opartych na Windows Forms można używać formantów Windows Presentation Foundation (WPF). Chociaż są to dwie różne technologie wyświetlania, działają bezproblemowo.

Projektant formularzy systemu Windows w programie Visual Studio udostępnia środowisko projektowania wizualnego do hostowania formantów Windows Presentation Foundation. Kontrolka WPF jest hostowana przez specjalną kontrolkę Windows Forms o nazwie <xref:System.Windows.Forms.Integration.ElementHost>. Ta kontrolka umożliwia uczestnictwo formantu WPF w układzie formularza oraz odbieranie komunikatów z klawiatury i myszy. W czasie projektowania można rozmieścić kontrolkę <xref:System.Windows.Forms.Integration.ElementHost> tak samo jak każda kontrolka Windows Forms.

Można również użyć formantów Windows Forms w aplikacjach opartych na platformie WPF. Aby uzyskać więcej informacji, zobacz [Designing XAML in Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).

## <a name="see-also"></a>Zobacz także

- [WPF i Windows Forms międzyoperacyjności](../../wpf/advanced/wpf-and-windows-forms-interoperation.md)
