---
title: "Jak ustalić jaka wersja WPF jest zainstalowana"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cf58e8e8ade7382d8a897a3ec59bef0c810a48bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a>Jak ustalić jaka wersja WPF jest zainstalowana
Numer wersji dla bieżącej wersji zainstalowanego [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] znajduje się w **rejestru**.  
  
 Aby określić numer wersji:  
  
1.  Na **Start** menu, kliknij przycisk **Uruchom**.  
  
2.  W **Otwórz**, typ **regedit.exe**.  
  
3.  Otwórz następujący klucz:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Numer wersji jest zapisany w **wersji** wartość.
