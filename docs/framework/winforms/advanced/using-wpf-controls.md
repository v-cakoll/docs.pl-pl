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
ms.openlocfilehash: 5ea92b24a2ca30c0ad137d83c8f521a952ad0c6b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658500"
---
# <a name="use-wpf-controls-in-windows-forms-apps"></a>Korzystanie z formantów WPF w aplikacjach Windows Forms

W aplikacjach opartych na Windows Forms można używać formantów Windows Presentation Foundation (WPF). Chociaż są to dwie różne technologie wyświetlania, działają bezproblemowo.

Projektant formularzy systemu Windows w programie Visual Studio udostępnia środowisko projektowania wizualnego do hostowania formantów Windows Presentation Foundation. Kontrolka WPF jest hostowana przez specjalną kontrolkę Windows Forms o <xref:System.Windows.Forms.Integration.ElementHost>nazwie. Ta kontrolka umożliwia uczestnictwo formantu WPF w układzie formularza oraz odbieranie komunikatów z klawiatury i myszy. W czasie projektowania można rozmieścić <xref:System.Windows.Forms.Integration.ElementHost> kontrolkę tak samo jak w przypadku każdej kontrolki Windows Forms.

Można również użyć formantów Windows Forms w aplikacjach opartych na platformie WPF. Aby uzyskać więcej informacji, zobacz [Designing XAML in Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).

## <a name="see-also"></a>Zobacz także

- [WPF i Windows Forms międzyoperacyjności](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)
