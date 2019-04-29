---
title: Format schowka nie jest prawidłowy
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: 5ec077be30b0afc8917d431dc9bd73c8dd41be89
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649871"
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
