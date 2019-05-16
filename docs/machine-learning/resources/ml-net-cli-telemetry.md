---
title: Zbieranie danych telemetrycznych przez interfejs wiersza polecenia w strukturze ML.NET
description: Dowiedz się więcej o funkcje telemetrii strukturze ML.NET interfejsu wiersza polecenia, które zbierają użycia informacje do analizy danych, które są zbierane i jak go wyłączyć. Ponadto Znajdź łącza do umowy licencyjnej .NET i informacje o zgodności z GDPR firmy Microsoft.
ms.topic: conceptual
ms.date: 05/05/2019
ms.custom: ''
ms.openlocfilehash: 36f4af48615e2e3247f8e21343d0a00519ba1c0a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645022"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a>Zbieranie danych telemetrycznych przez interfejs wiersza polecenia strukturze ML.NET

[Interfejsu wiersza polecenia w strukturze ML.NET](http://aka.ms/mlnet-cli) obejmuje funkcję dane telemetryczne, które zbiera anonimowe dane użycia zagregowanych do użycia przez firmę Microsoft.

## <a name="how-microsoft-uses-the-data"></a>Jak firma Microsoft używa danych

Zespół pracujący nad produktem używa danych telemetrycznych interfejsu wiersza polecenia w strukturze ML.NET pomagające zrozumieć, jak poprawić narzędzia. Na przykład użycie klientów rzadko określonej usługi machine learning zadania, zespół pracujący nad produktem bada dlaczego i używa ustalenia, aby określić priorytety rozwój funkcji. Interfejs wiersza polecenia w strukturze ML.NET telemetrii pomaga również debugowanie problemów, takich jak awarie i anomalii kodu. 

Gdy zespół pracujący nad produktem ocenia te szczegółowe informacje, wiemy również, że nie każdy chce wysyłać te dane. [Dowiedz się, jak wyłączyć telemetrię.](#opt-out-of-data-collection)

## <a name="scope"></a>Scope

`mlnet` Polecenie uruchamia strukturze ML.NET interfejsu wiersza polecenia, ale samo polecenie nie zbiera dane telemetryczne.

Dane telemetryczne *nie włączono* po uruchomieniu `mlnet` polecenia żadne inne polecenie dołączone. Na przykład:

- `mlnet`
- `mlnet --help`

Dane telemetryczne *włączono* po uruchomieniu [polecenia interfejsu wiersza polecenia w strukturze ML.NET](../reference/ml-net-cli-reference.md), takich jak `mlnet auto-train`.

## <a name="opt-out-of-data-collection"></a>Zrezygnować ze zbierania danych

Funkcja telemetrii interfejsu wiersza polecenia w strukturze ML.NET jest włączona domyślnie.

Zrezygnować z funkcji danych telemetrycznych przez ustawienie `DOTNET_CLI_TELEMETRY_OPTOUT` zmiennej środowiskowej, aby `1` lub `true`. Ta zmienna środowiskowa globalnie stosuje się do narzędzia wiersza polecenia platformy .NET.

## <a name="data-points-collected"></a>Zebranych punktów danych

Ta funkcja zbiera następujące dane:

- Jakie polecenia została wywołana, takich jak `auto-train`
- Nazwy parametrów wiersza polecenia używane (czyli "Nazwa zestawu danych, nazwę kolumny etykiety, zadania uczenia maszynowego, ścieżkę wyjściową, max eksploracji w czasie, poziom szczegółowości")
- Mieszana adres MAC: kryptograficznie (SHA256) anonimowe i unikatowy identyfikator dla maszyny
- Sygnatura czasowa wywołania
- Trzy octet adres IP (nie pełnemu) używane tylko w celu określenia lokalizacji geograficznej
- Nazwy wszystkich argumentów/parametry używane. Nie odbiorcy wartości, takich jak ciągi
- Nazwa zestawu danych w formie skrótu pliku
- Przedział rozmiaru pliku zestawu danych
- Wersja systemu operacyjnego i
- Wartość parametru--zadań: Podzielone wartości, takich jak `regression`, `binary-classification`, i `multiclass-classification`
- Wersja interfejsu wiersza polecenia w strukturze ML.NET (tj. 0.3.27703.4)

Dane są przesyłane w bezpieczny sposób do serwerów firmy Microsoft przy użyciu [usługi Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technologii, przechowywane w obszarze ograniczony dostęp i używane w ramach rygorystyczne kontrole zabezpieczeń z bezpiecznym [usługi Azure Storage](https://azure.microsoft.com/services/storage/) systemów.

### <a name="data-points-not-collected"></a>Nie zebrano punktów danych
Funkcja telemetrii *nie* zbierania:
- dane osobowe, takich jak nazwy użytkowników
- nazwy plików zestawu danych
- dane z plików zestawu danych

Jeśli podejrzewasz, że zbiera dane telemetryczne interfejsu wiersza polecenia w strukturze ML.NET poufne dane, lub że dane są insecurely lub niewłaściwie obsługiwane, Prześlij zgłoszenie do [strukturze ML.NET](https://github.com/dotnet/machinelearning) repozytorium na potrzeby badania.

## <a name="license"></a>Licencja

Dystrybucja Microsoft interfejsu wiersza polecenia w strukturze ML.NET ma licencję za pomocą [postanowienia licencyjne dotyczące oprogramowania firmy Microsoft: Microsoft .NET Library](https://aka.ms/dotnet-core-eula). Aby uzyskać szczegółowe informacje dotyczące zbierania i przetwarzania danych zobacz sekcję zatytułowaną "Dane".

## <a name="disclosure"></a>Ujawnienie

Przy pierwszym uruchomieniu [polecenia interfejsu wiersza polecenia w strukturze ML.NET](../reference/ml-net-cli-reference.md) takich jak `mlnet auto-train`, narzędzia interfejsu wiersza polecenia w strukturze ML.NET Wyświetla tekst ujawnienie, który informuje, jak zrezygnować z danych telemetrycznych. Tekst może się nieco różnić w zależności od wersji korzystasz z interfejsu wiersza polecenia.

## <a name="see-also"></a>Zobacz także
- [Dokumentacja interfejsu wiersza polecenia w strukturze ML.NET](../reference/ml-net-cli-reference.md)
- [Postanowienia licencyjne dotyczące oprogramowania firmy Microsoft: Microsoft .NET Library](https://aka.ms/dotnet-core-eula)
- [Ochrona prywatności w firmie Microsoft](https://www.microsoft.com/en-us/trustcenter/privacy/)
- [Poufności informacji firmy Microsoft](https://privacy.microsoft.com/en-us/privacystatement)
