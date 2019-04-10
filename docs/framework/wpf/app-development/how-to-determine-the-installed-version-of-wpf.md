---
title: 'Instrukcje: Ustalanie zainstalowanej wersji WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
ms.openlocfilehash: ffbd9a4c7f66dff9c8773dff4259551e20aa963d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59305679"
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a>Instrukcje: Ustalanie zainstalowanej wersji WPF
Numer wersji dla bieżącej zainstalowanej wersji [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] znajduje się w **rejestru**.  
  
 Aby znaleźć numer wersji:  
  
1. Na **Start** menu, kliknij przycisk **Uruchom**.  
  
2. W **Otwórz**, typ **regedit.exe**.  
  
3. Otwórz następujący klucz:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Numer wersji jest przechowywany w **wersji** wartość.
