---
title: Zbieranie danych telemetrycznych za pomocą interfejsu wiersza polecenia ML.NET
description: Dowiedz się więcej o funkcjach telemetrycznych interfejsu wiersza polecenia ML.NET, które zbierają informacje o użyciu do analizy, zbierane dane i jak je wyłączyć. Znajdź także linki do umowy licencyjnej platformy .NET oraz informacje o zgodności z programem Microsoft Rodo.
ms.topic: conceptual
ms.date: 05/05/2019
ms.custom: ''
ms.openlocfilehash: eab1e37d7d0d47251c4f92422730b105cf2db265
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433793"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a>Zbieranie danych telemetrycznych za pomocą interfejsu wiersza polecenia ML.NET

[Interfejs wiersza polecenia ml.NET](https://aka.ms/mlnet-cli) zawiera funkcję telemetrii, która zbiera anonimowe dane użycia, które są agregowane na użytek firmy Microsoft.

## <a name="how-microsoft-uses-the-data"></a>Jak firma Microsoft używa danych

Zespół produktu używa danych telemetrycznych interfejsu wiersza polecenia ML.NET, aby pomóc zrozumieć, jak ulepszyć narzędzia. Na przykład jeśli klienci rzadko wykorzystują określone zadanie uczenia maszynowego, zespół produktu bada dlaczego i korzysta z wyników, aby określić priorytety projektowania funkcji. Dane telemetryczne interfejsu wiersza polecenia ML.NET pomagają również debugować problemy, takie jak awarie i anomalie w kodzie. 

Gdy zespół produktu docenia ten wgląd, wie również, że nie wszyscy chcą wysyłać te dane. [Dowiedz się, jak wyłączyć telemetrię.](#opt-out-of-data-collection)

## <a name="scope"></a>Scope

`mlnet` Polecenie uruchamia interfejs wiersza polecenia ml.NET, ale samo polecenie nie zbiera danych telemetrycznych.

Funkcja telemetrii *nie jest włączona* po uruchomieniu `mlnet` polecenia bez innego dołączonego polecenia. Na przykład:

- `mlnet`
- `mlnet --help`

Funkcja telemetrii *jest włączona* po uruchomieniu [polecenia ml.NET CLI](../reference/ml-net-cli-reference.md), takiego `mlnet auto-train`jak.

## <a name="opt-out-of-data-collection"></a>Rezygnacja z zbierania danych

Funkcja telemetrii interfejsu wiersza polecenia ML.NET jest domyślnie włączona.

Rezygnacja z funkcji telemetrii przez ustawienie `DOTNET_CLI_TELEMETRY_OPTOUT` zmiennej środowiskowej `1` na `true`lub. Ta zmienna środowiskowa jest stosowana globalnie do narzędzia interfejsu wiersza polecenia platformy .NET.

## <a name="data-points-collected"></a>Zebrane punkty danych

Funkcja zbiera następujące dane:

- Jakie polecenie zostało wywołane, na przykład`auto-train`
- Używane nazwy parametrów wiersza polecenia (tj. "DataSet-Name, Label-column-name, ml-Task, Output-Path, Max-Learning-Time, szczegółowości")
- Skrótowy adres MAC: kryptograficzny (SHA256) anonimowy i unikatowy identyfikator dla komputera
- Sygnatura czasowa wywołania
- Trzy oktetowe adresy IP (nie pełny adres IP) używane tylko do określania lokalizacji geograficznej
- Nazwa wszystkich używanych argumentów/parametrów. Nie wartości klienta, takie jak ciągi
- Nazwa pliku zestawu danych skrótów
- Zasobnik rozmiaru pliku zestawu danych
- System operacyjny i wersja
- Wartość--parametru zadania: Kategorii wartości, takie jak `regression`, `binary-classification`i`multiclass-classification`
- Wersja interfejsu wiersza polecenia ML.NET (np. 0.3.27703.4)

Dane są bezpiecznie przesyłane do serwerów firmy Microsoft przy użyciu technologii [Application Insights platformy Azure](https://azure.microsoft.com/services/application-insights/) , w ramach ograniczonego dostępu i stosowane w ramach ścisłej kontroli zabezpieczeń z bezpiecznych systemów [usługi Azure Storage](https://azure.microsoft.com/services/storage/) .

### <a name="data-points-not-collected"></a>Punkty danych nie są zbierane
Funkcja telemetrii *nie* zbiera:
- dane osobowe, takie jak nazwy użytkowników
- nazwy plików DataSet
- dane z plików DataSet

Jeśli podejrzewasz, że Telemetria interfejsu wiersza polecenia ML.NET zbiera poufne dane lub że dane są w sposób niezabezpieczony lub niewłaściwie obsłużony, należy rozwiązać problem w repozytorium [ml.NET](https://github.com/dotnet/machinelearning) w celu zbadania.

## <a name="license"></a>Licencja

ML.NET interfejs wiersza polecenia firmy Microsoft do dystrybucji jest licencjonowany za pomocą [postanowień licencyjnych dotyczących oprogramowania firmy Microsoft: Biblioteka](https://aka.ms/dotnet-core-eula)Microsoft .NET. Aby uzyskać szczegółowe informacje na temat zbierania i przetwarzania danych, zobacz sekcję zatytułowaną "dane".

## <a name="disclosure"></a>Mogąc

Gdy po raz pierwszy uruchomisz [polecenie interfejsu wiersza polecenia ml.NET](../reference/ml-net-cli-reference.md) , takie jak `mlnet auto-train`, narzędzie ml.NET CLI wyświetla tekst, który informuje, jak zrezygnować z telemetrii. Tekst może się nieco różnić w zależności od używanej wersji interfejsu wiersza polecenia.

## <a name="see-also"></a>Zobacz także
- [Dokumentacja interfejsu wiersza polecenia ML.NET](../reference/ml-net-cli-reference.md)
- [Postanowienia licencyjne dotyczące oprogramowania firmy Microsoft: Biblioteka Microsoft .NET](https://aka.ms/dotnet-core-eula)
- [Prywatność w firmie Microsoft](https://www.microsoft.com/trustcenter/privacy/)
- [Zasady zachowania poufności informacji firmy Microsoft](https://privacy.microsoft.com/privacystatement)
