---
title: Format schowka nie jest prawidłowy
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: eef16096b269902dbaca6a344abf4c5f6a504fb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="clipboard-format-is-not-valid"></a>Format schowka nie jest prawidłowy
Określony format Schowka jest niezgodna z wykonywanej metody. Wśród możliwych przyczyn tego błędu są:  
  
-   Korzystanie ze Schowka `GetText` lub `SetText` metody przy użyciu formatu Schowka innych niż `vbCFText` lub `vbCFLink`.  
  
-   Korzystanie ze Schowka `GetData` lub `SetData` metody przy użyciu formatu Schowka innych niż `vbCFBitmap`, `vbCFDIB`, lub `vbCFMetafile`.  
  
-   Przy użyciu `DataObject``GetData` metody lub `SetData` metody przy użyciu formatu Schowka w zakresie zarezerwowane przez Microsoft Windows dla zarejestrowanego formatów (& HC000 - & HFFFF), podczas tego formatu Schowka nie został zarejestrowany w usłudze Microsoft Windows.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Usuń nieprawidłowy format i określ prawidłowa.  
  
## <a name="see-also"></a>Zobacz też  
 [Schowek: dodawanie innych formatów](/cpp/mfc/clipboard-adding-other-formats)
