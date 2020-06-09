---
title: System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
ms.date: 03/30/2017
ms.assetid: 9eb311da-fdcc-4dd3-9d85-05b3280dfdda
ms.openlocfilehash: e11b376924ee74e5d0d67da0cac59af41655dc44
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594078"
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a>System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
Nie można odebrać wiadomości kanałem HTTP.  
  
## <a name="description"></a>Opis  
 Ten ślad może być emitowany jako ostrzeżenie lub błąd. W obu przypadkach ślad jest emitowany, gdy nie znaleziono zgodnego odbiornika dla przychodzącego żądania HTTP, a żądanie HTTP zostanie odrzucone. Może się tak zdarzyć, ponieważ czasownik HTTP żądania nie został rozpoznany przez żaden odbiornik HTTP lub żaden odbiornik nie nasłuchuje na adresie, którego dotyczy żądanie. Ślad jest emitowany jako ostrzeżenie w przypadku samodzielnego użycia i jako błąd, gdy usługa jest hostowana w usługach IIS.  
  
## <a name="see-also"></a>Zobacz też

- [Śledzenie](index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](using-tracing-to-troubleshoot-your-application.md)
- [Administracja i Diagnostyka](../index.md)
