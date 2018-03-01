---
title: "Format schowka nie jest prawidłowy"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e7adc417d962de35272319d7dc976b237c7e2b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="clipboard-format-is-not-valid"></a>Format schowka nie jest prawidłowy
Określony format Schowka jest niezgodna z wykonywanej metody. Wśród możliwych przyczyn tego błędu są:  
  
-   Korzystanie ze Schowka `GetText` lub `SetText` metody przy użyciu formatu Schowka innych niż `vbCFText` lub `vbCFLink`.  
  
-   Korzystanie ze Schowka `GetData` lub `SetData` metody przy użyciu formatu Schowka innych niż `vbCFBitmap`, `vbCFDIB`, lub `vbCFMetafile`.  
  
-   Przy użyciu `DataObject``GetData` metody lub `SetData` metody przy użyciu formatu Schowka w zakresie zarezerwowane przez Microsoft Windows dla zarejestrowanego formatów (& HC000 - & HFFFF), podczas tego formatu Schowka nie został zarejestrowany w usłudze Microsoft Windows.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Usuń nieprawidłowy format i określ prawidłowa.  
  
## <a name="see-also"></a>Zobacz też  
 [Schowek: Dodawanie innych formatów](/cpp/mfc/clipboard-adding-other-formats)
