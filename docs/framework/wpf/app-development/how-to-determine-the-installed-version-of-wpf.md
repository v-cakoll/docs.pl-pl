---
title: Określanie zainstalowanej wersji platformy WPF
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
ms.openlocfilehash: 8fc5c380779891b44b7c4f7f8aeb5ed119d8b768
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735695"
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a>Jak ustalić jaka wersja WPF jest zainstalowana
Numer wersji aktualnie zainstalowanej wersji [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] znajduje się w **rejestrze**.  
  
 Aby znaleźć numer wersji:  
  
1. W menu **Start** kliknij polecenie **Uruchom**.  
  
2. W obszarze **Otwórz**wpisz **regedit. exe**.  
  
3. Otwórz następujący klucz:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 Numer wersji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest przechowywany w wartości **wersji** .
