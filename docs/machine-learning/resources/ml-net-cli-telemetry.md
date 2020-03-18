---
title: Zbieranie danych telemetrycznych przez ML.NET CLI
description: Dowiedz się więcej o ML.NET funkcji telemetrii wiersza wiersza, które zbierają informacje o użyciu do analizy, jakie dane są zbierane i jak je wyłączyć. Ponadto znajdź łącza do umowy licencyjnej .NET i informacje o zgodności z RODO firmy Microsoft.
ms.topic: conceptual
ms.date: 09/03/2019
ms.custom: mlnet-tooling
ms.openlocfilehash: 99e11acba343cc689c3219ca9316144fc62cd618
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78849747"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a>Zbieranie danych telemetrycznych przez ML.NET CLI

[ML.NET CLI](https://aka.ms/mlnet-cli) zawiera funkcję telemetrii, która zbiera anonimowe dane użycia, które są agregowane do użytku przez firmę Microsoft.

## <a name="how-microsoft-uses-the-data"></a>Jak firma Microsoft wykorzystuje dane

Zespół produktu używa danych telemetrycznych ML.NET CLI, aby pomóc w zrozumieniu, jak ulepszyć narzędzia. Na przykład jeśli klienci rzadko używają określonego zadania uczenia maszynowego, zespół produktu bada, dlaczego i używa wyników do ustalania priorytetów tworzenia funkcji. ML.NET telemetrii interfejsu i telewizji pomaga również w debugowaniu problemów, takich jak awarie i anomalie kodu.

Podczas gdy zespół produktów docenia tę wiedzę, wiemy również, że nie każdy chce wysłać te dane. [Dowiedz się, jak wyłączyć telemetrię.](#opt-out-of-data-collection)

## <a name="scope"></a>Zakres

Polecenie `mlnet` uruchamia ML.NET CLI, ale samo polecenie nie zbiera danych telemetrycznych.

Telemetria *nie jest włączona* po uruchomieniu `mlnet` polecenia bez innego polecenia dołączone. Przykład:

- `mlnet`
- `mlnet --help`

Telemetria *jest włączona* po uruchomieniu [polecenia ML.NET wiersza polecenia ,](../reference/ml-net-cli-reference.md)na przykład . `mlnet auto-train`

## <a name="opt-out-of-data-collection"></a>Rezygnacja z gromadzenia danych

Funkcja telemetrii ML.NET CLI jest domyślnie włączona.

Zrezygnuj z `MLDOTNET_CLI_TELEMETRY_OPTOUT` funkcji telemetrii, ustawiając zmienną środowiskową na `1` lub `true`. Ta zmienna środowiskowa ma zastosowanie globalnie do narzędzia ML.NET CLI.

## <a name="data-points-collected"></a>Zebrane punkty danych

Funkcja zbiera następujące dane:

- Jakie polecenie zostało wywołane, takie jak`auto-train`
- Używane nazwy parametrów wiersza polecenia (czyli "nazwa zestawu danych, nazwa kolumny etykiety, ml-task, ścieżka wyjścia, czas max-eksploracji, szczegółowość")
- Hashed adres MAC: kryptograficznie (SHA256) anonimowy i unikalny identyfikator dla komputera
- Sygnatura czasowa wywołania
- Trzy oktetowe adres IP (nie pełny adres IP) używane tylko do określania lokalizacji geograficznej
- Nazwa wszystkich użytych argumentów/parametrów. Nie wartości klienta, takie jak ciągi znaków
- Haszowane nazwy pliku zestawu danych
- Zasobnik rozmiaru pliku zestawu danych
- System operacyjny i wersja
- Wartość parametru --task: Wartości kategorii, takie jak `regression`, `binary-classification`, i`multiclass-classification`
- ML.NET wersji CLI (czyli 0.3.27703.4)

Dane są bezpiecznie wysyłane do serwerów firmy Microsoft przy użyciu technologii [usługi Azure Application Insights,](https://azure.microsoft.com/services/application-insights/) przechowywane w ramach ograniczonego dostępu i używane pod ścisłymi kontrolami zabezpieczeń z bezpiecznych systemów [usługi Azure Storage.](https://azure.microsoft.com/services/storage/)

### <a name="data-points-not-collected"></a>Punkty danych nie są zbierane

Funkcja telemetrii *nie* zbiera:

- danych osobowych, takich jak nazwy użytkowników
- nazwy plików zestawu danych
- dane z plików zestawu danych

Jeśli podejrzewasz, że ML.NET telemetrii cli zbiera poufne dane lub że dane są niebezpiecznie lub niewłaściwie obsługiwane, zgłoś problem w repozytorium [ML.NET](https://github.com/dotnet/machinelearning) w celu zbadania.

## <a name="license"></a>Licencja

Dystrybucja ML.NET CLI firmy Microsoft jest licencjonowana z [postanowieniami licencyjnymi firmy Microsoft: Microsoft .NET Library](https://aka.ms/dotnet-core-eula). Szczegółowe informacje na temat gromadzenia i przetwarzania danych można znaleźć w sekcji zatytułowanej "Dane".

## <a name="disclosure"></a>Ujawnienie

Po pierwszym uruchomieniu polecenia ML.NET `mlnet auto-train` [CLI,](../reference/ml-net-cli-reference.md) takie jak , narzędzie ML.NET CLI wyświetla tekst ujawnienia, który informuje, jak zrezygnować z telemetrii. Tekst może się nieznacznie różnić w zależności od używanej wersji kaliów.

## <a name="see-also"></a>Zobacz też

- [ML.NET odwołanie cli](../reference/ml-net-cli-reference.md)
- [Postanowienia licencyjne dotyczące oprogramowania firmy Microsoft: Microsoft .NET Library](https://aka.ms/dotnet-core-eula)
- [Prywatność w firmie Microsoft](https://www.microsoft.com/trustcenter/privacy/)
- [Oświadczenie o ochronie prywatności w firmie Microsoft](https://privacy.microsoft.com/privacystatement)
