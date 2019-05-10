---
title: Format schowka nie jest prawidłowy
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: 15bc530d1030a8c4d720321ea249fdd7fb6cd8b6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623096"
---
# <a name="clipboard-format-is-not-valid"></a>Format schowka nie jest prawidłowy
Określony format Schowka jest niezgodna z wykonywanej metody. Wśród możliwych przyczyn tego błędu są:  
  
- Korzystanie ze Schowka `GetText` lub `SetText` metody z formatu Schowka w innych niż `vbCFText` lub `vbCFLink`.  
  
- Korzystanie ze Schowka `GetData` lub `SetData` metody z formatu Schowka w innych niż `vbCFBitmap`, `vbCFDIB`, lub `vbCFMetafile`.  
  
- Za pomocą `GetData` lub `SetData` metody `DataObject` za pomocą formatu Schowka w zakresie zarezerwowane przez program Microsoft Windows dla zarejestrowanego formatów (& HC000 - & HFFFF), gdy ten format schowka nie został zarejestrowany za pomocą programu Microsoft Windows .  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Usuń nieprawidłowy format i określ prawidłowa.  
  
## <a name="see-also"></a>Zobacz także

- [Schowek: dodawanie innych kontrolek](/cpp/mfc/clipboard-adding-other-formats)
