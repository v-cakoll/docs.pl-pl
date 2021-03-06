---
title: Migracja i współdziałanie
ms.date: 03/23/2020
f1_keywords:
- AutoGeneratedOrientationPage
helpviewer_keywords:
- Windows Presentation Foundation [WPF], interoperability
- WPF [WPF], migration
- Windows Forms controls [WPF interoperability]
- controls [WPF interoperability]
- Windows Presentation Foundation [WPF], migration
- interoperability [WPF]
- WPF [WPF], interoperability
- migration [WPF]
ms.assetid: d655de05-bf63-4814-bc64-6b3be01c70a2
ms.openlocfilehash: 180ece4f178406c6c3e704ecadaa9a72955ec038
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249054"
---
# <a name="migration-and-interoperability"></a>Migracja i współdziałanie

Ta strona zawiera łącza do dokumentów, które [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] omawiają sposób implementacji współpracy między aplikacjami i innymi typami aplikacji systemu Microsoft Windows.

## <a name="in-this-section"></a>W tej sekcji

[Typy migrowane z WPF do pliku System.Xaml](types-migrated-from-wpf-to-system.md)\
[Interoperacyjności formularzy WPF i windows](wpf-and-windows-forms-interoperation.md)\
[Interoperacyjności WPF i Win32](wpf-and-win32-interoperation.md)\
[WPF i Direct3D9 — współdziałanie](wpf-and-direct3d9-interoperation.md)

## <a name="reference"></a>Tematy pomocy

| Termin                                                     | Definicja                                                                                                                                                                                                                                                                                                                                                                                                  |
|----------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <xref:System.Windows.Forms.Integration.WindowsFormsHost> | Element, którego można użyć do hosta formantu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Windows Forms jako elementu strony.                                                                                                                                                                                                                                      |
| <xref:System.Windows.Forms.Integration.ElementHost>      | Formant Formularze systemu Windows, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] którego można używać do hosta formantu.                                                                                                                                                                                                                                                                 |
| <xref:System.Windows.Interop.HwndSource>                 | Hostuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] region w aplikacji Win32.                                                                                                                                                                                                                                                                                |
| <xref:System.Windows.Interop.HwndHost>                   | Klasa podstawowa dla <xref:System.Windows.Forms.Integration.WindowsFormsHost>, definiuje niektóre podstawowe funkcje, które wszystkie technologie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oparte na HWND używać podczas hostowane przez aplikację. Podklasa to do hostowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] okna Win32 w aplikacji. |
| <xref:System.Windows.Interop.BrowserInteropHelper>       | Klasa pomocnika dla warunków raportowania środowiska [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przeglądarki dla aplikacji, która jest obsługiwana przez przeglądarkę.                                                                                                                                                                                                         |

## <a name="related-sections"></a>Sekcje pokrewne
