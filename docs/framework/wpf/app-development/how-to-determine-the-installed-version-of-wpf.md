---
title: 'Instrukcje: Ustalanie zainstalowanej wersji WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
ms.openlocfilehash: ffbd9a4c7f66dff9c8773dff4259551e20aa963d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052459"
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a>Instrukcje: Ustalanie zainstalowanej wersji WPF
Numer wersji dla bieżącej zainstalowanej wersji [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] znajduje się w **rejestru**.  
  
 Aby znaleźć numer wersji:  
  
1. Na **Start** menu, kliknij przycisk **Uruchom**.  
  
2. W **Otwórz**, typ **regedit.exe**.  
  
3. Otwórz następujący klucz:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Numer wersji jest przechowywany w **wersji** wartość.
