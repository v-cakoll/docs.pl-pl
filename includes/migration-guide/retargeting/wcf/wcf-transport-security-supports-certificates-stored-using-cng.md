---
ms.openlocfilehash: 5c09bee92f679cd7e7a95cd23d5ce0ca9b57170c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614742"
---
### <a name="wcf-transport-security-supports-certificates-stored-using-cng"></a>Zabezpieczenia transportu WCF obsługują certyfikaty przechowywane przy użyciu CNG

#### <a name="details"></a>Szczegóły

Począwszy od aplikacji przeznaczonych dla .NET Framework 4.6.2, zabezpieczenia transportu WCF obsługują certyfikaty przechowywane przy użyciu biblioteki kryptografii systemu Windows (CNG). Ta obsługa jest ograniczona do certyfikatów z kluczem publicznym o wykładniku nie większym niż 32 bitów. Gdy aplikacja jest przeznaczona dla .NET Framework 4.6.2, ta funkcja jest domyślnie włączona. We wcześniejszych wersjach .NET Framework próba użycia certyfikatów x509 z dostawcą magazynu kluczy CSG zgłasza wyjątek.

#### <a name="suggestion"></a>Sugestia

Aplikacje, które są przeznaczone dla .NET Framework 4.6.1 i wcześniejszych, ale działają na .NET Framework 4.6.2 mogą włączyć obsługę certyfikatów CNG, dodając następujący wiersz do `<runtime>` sekcji pliku app.config lub web.config:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableCngCertificates=false" />
</runtime>
```

Można to również zrobić programowo przy użyciu następującego kodu:

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificate";

AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

Należy zauważyć, że ze względu na tę zmianę wszelki kod obsługi wyjątków, który zależy od próby zainicjowania bezpiecznej komunikacji z certyfikatem CNG do niepowodzenia, nie będzie już wykonywany.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.6.2       |
| Typ    | Przekierowanie |
