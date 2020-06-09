---
title: System.ServiceModel.MessageClosedAgain
ms.date: 03/30/2017
ms.assetid: 24c274d4-65cd-4c91-9869-bc6eb34ef979
ms.openlocfilehash: d341953b8e12b14e6a3fe8a477c16a1b3a4454ae
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84580440"
---
# <a name="systemservicemodelmessageclosedagain"></a>System.ServiceModel.MessageClosedAgain
System.ServiceModel.MessageClosedAgain  
  
## <a name="description"></a>Opis  
 Komunikat został zamknięty ponownie.  
  
 Komunikat powinien być zamknięty tylko raz. Jeśli ślad jest emitowany w kodzie rozszerzenia użytkownika, oznacza to, że kod rozszerzenia użytkownika zamyka komunikat, który został już zamknięty. Jeśli ślad jest emitowany za pomocą kodu produktu, oznacza to, że kod rozszerzenia użytkownika może potencjalnie zamknąć komunikat zbyt wcześnie.  
  
## <a name="see-also"></a>Zobacz też

- [Śledzenie](index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](using-tracing-to-troubleshoot-your-application.md)
- [Administracja i Diagnostyka](../index.md)
