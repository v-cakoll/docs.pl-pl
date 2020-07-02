---
ms.openlocfilehash: 3aafb14b65f7c0f9e5d77927809547f9d4b96e1c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620368"
---
### <a name="error-codes-for-maxrequestlength-or-maxreceivedmessagesize-are-different"></a>Kody błędów dla 'Maxrequestlength lub maxReceivedMessageSize są różne

#### <a name="details"></a>Szczegóły

Komunikaty w usługach sieci Web WCF hostowanych w Internet Information Services (IIS) lub ASP.NET Development Server, które przekraczają 'Maxrequestlength (w ASP.NET) lub maxReceivedMessageSize (w programie WCF), mają różne błędy codeThe kod stanu HTTP został zmieniony z 400 (złe żądanie) na 413 (jednostka żądania jest zbyt duża) i komunikaty, które przekraczają albo wartość parametru 'Maxrequestlength lub maxReceivedMessageSize, zgłaszają <xref:System.ServiceModel.ProtocolException?displayProperty=fullName> wyjątek. Obejmuje to przypadki, w których tryb transferu jest przesyłany strumieniowo.

#### <a name="suggestion"></a>Sugestia

Ta zmiana ułatwia debugowanie w przypadkach, gdy długość komunikatu przekracza limity dozwolone przez ASP.NET lub WCF. Należy zmodyfikować każdy kod, który wykonuje przetwarzanie na podstawie kodu stanu HTTP 400.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
