---
title: Jak ustalić jaka wersja WPF jest zainstalowana
ms.date: 03/30/2017
helpviewer_keywords:
- version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
ms.openlocfilehash: c59fa0d0a4d94c6e6a2ab72a4cd7a3c066649fb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545854"
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a>Jak ustalić jaka wersja WPF jest zainstalowana
Numer wersji dla bieżącej wersji zainstalowanego [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] znajduje się w **rejestru**.  
  
 Aby określić numer wersji:  
  
1.  Na **Start** menu, kliknij przycisk **Uruchom**.  
  
2.  W **Otwórz**, typ **regedit.exe**.  
  
3.  Otwórz następujący klucz:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Numer wersji jest zapisany w **wersji** wartość.
