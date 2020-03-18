---
title: Zasoby szkoleniowe platformy Azure dla konstruktora modeli
description: Przewodnik po zasobach dla usługi Azure Machine Learning
ms.topic: reference
ms.date: 02/27/2020
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: a19e13955d0eaea344109eb817f3a3959c3dd883
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185821"
---
# <a name="model-builder-azure-training-resources"></a>Zasoby szkoleniowe platformy Azure dla konstruktora modeli

Poniżej przedstawiono przewodnik, który pomoże Ci dowiedzieć się więcej o zasobach używanych do uczenia modeli na platformie Azure za pomocą konstruktora modeli.

## <a name="what-is-an-azure-machine-learning-experiment"></a>Co to jest eksperyment usługi Azure Machine Learning?

Eksperyment usługi Azure Machine Learning to zasób, który należy utworzyć przed uruchomieniem szkolenia dla konstruktora modeli na platformie Azure.

Eksperyment hermetyzuje konfigurację i wyniki dla co najmniej jednego przebiegu szkolenia uczenia maszynowego. Eksperymenty należą do określonego obszaru roboczego. Po pierwszym utworzeniu eksperymentu jego nazwa jest rejestrowana w obszarze roboczym. Wszystkie kolejne przebiegi - jeśli używana jest ta sama nazwa eksperymentu - są rejestrowane jako część tego samego eksperymentu. W przeciwnym razie zostanie utworzony nowy eksperyment.

## <a name="what-is-an-azure-machine-learning-workspace"></a>Co to jest obszar roboczy usługi Azure Machine Learning?

Obszar roboczy to zasób usługi Azure Machine Learning, który zapewnia centralne miejsce dla wszystkich zasobów usługi Azure Machine Learning i artefaktów utworzonych w ramach przebiegu szkolenia.

Aby utworzyć obszar roboczy usługi Azure Machine Learning, wymagane są następujące elementy:

- Nazwa: Nazwa obszaru roboczego od 3 do 33 znaków. Nazwy mogą zawierać tylko znaki alfanumeryczne i łączniki.
- Region: lokalizacja geograficzna centrum danych, w którym obszar roboczy i zasoby są wdrażane. Zaleca się wybranie lokalizacji w pobliżu miejsca, w którym znajdujesz się w użytkowniku lub u jego klientach.
- Grupa zasobów: kontener zawierający wszystkie powiązane zasoby rozwiązania platformy Azure.

## <a name="what-is-an-azure-machine-learning-compute"></a>Co to jest obliczenia usługi Azure Machine Learning?

Obliczenia usługi Azure Machine Learning to oparta na chmurze maszyna wirtualna systemu Linux używana do szkolenia.

Aby utworzyć obszar roboczy usługi Azure Machine Learning, wymagane są następujące elementy:

- Nazwa: Nazwa obszaru roboczego od 2 do 16 znaków. Nazwy mogą zawierać tylko znaki alfanumeryczne i łączniki.
- Rozmiar obliczeń

    Konstruktor modeli może używać jednego z następujących typów obliczeń zoptymalizowanych pod kątem procesora GPU:

    | Rozmiar | Procesor wirtualny | Pamięć: GiB | Magazyn tymczasowy (SSD): GiB | Procesory GPU | Pamięć GPU: GiB | Maks. liczba dysków danych | Maksymalna liczba kart sieciowych |
    |---|---|---|---|---|---|---|---|
    | Standardowa_NC12   | 12 | 112 | 680  | 2 | 24 | 48 | 2 |
    | Standardowa_NC24   | 24 | 224 | 1440 | 4 | 48 | 64 | 4 |

    Odwiedź [dokumentację maszyn wirtualnych systemu Linux z serii NC,](https://docs.microsoft.com/azure/virtual-machines/nc-series?toc=/azure/virtual-machines/linux/toc.json&bc=/azure/virtual-machines/linux/breadcrumb/toc.json) aby uzyskać więcej informacji na temat typów obliczeń zoptymalizowanych pod kątem gpu.

## <a name="training"></a>Szkolenia

Szkolenie na platformie Azure jest dostępne tylko dla scenariusza klasyfikacji obrazów Konstruktora modeli. Algorytm używany do uczenia tych modeli jest deep sieci neuronowej na podstawie architektury ResNet50. Proces szkolenia zajmuje trochę czasu, a czas może się różnić w zależności od rozmiaru wybranej mocy obliczeniowej, a także ilości danych. Po raz pierwszy model jest przeszkolony, można oczekiwać nieco dłuższy czas szkolenia, ponieważ zasoby muszą być aprowizowane. Postęp przebiegów można śledzić, wybierając łącze "Monitorowanie bieżącego uruchomienia w witrynie Azure portal" w programie Visual Studio.

## <a name="results"></a>Wyniki

Po zakończeniu szkolenia do rozwiązania dodawane są dwa projekty z następującymi sufiksami:

- *ConsoleApp:* A C# .NET Core aplikacji konsoli, który zawiera kod startowy do tworzenia potoku przewidywania i dokonać prognoz.
- *Model:* A C# .NET Standardowa aplikacja, która zawiera modele danych, które definiują schemat danych modelu wejściowego i wyjściowego, a także następujące zasoby:

  - bestModel.onnx: Serializowana wersja modelu w formacie Open Neural Network Exchange (ONNX). ONNX jest formatem open source dla modeli AI, który obsługuje współdziałanie między platformami, takimi jak ML.NET, PyTorch i TensorFlow.
  - bestModelMap.json: Lista kategorii używanych podczas tworzenia prognoz do mapowania danych wyjściowych modelu do kategorii tekstu.
  - MLModel.zip: Serializowana wersja potoku prognozowania ML.NET, który używa serializowanej wersji modelu *bestModel.onnx* do tworzenia prognoz i map danych wyjściowych przy użyciu `bestModelMap.json` pliku.

## <a name="use-the-machine-learning-model"></a>Korzystanie z modelu uczenia maszynowego

I `ModelInput` `ModelOutput` klas w *projekcie model* zdefiniować schemat oczekiwanego wejścia modelu i danych wyjściowych odpowiednio.

W scenariuszu `ModelInput` klasyfikacji obrazu zawiera dwie kolumny:

- `ImageSource`: Ścieżka ciągu lokalizacji obrazu.
- `Label`: Rzeczywista kategoria, do której należy obraz. `Label`jest używany tylko jako dane wejściowe podczas szkolenia i nie musi być dostarczony podczas dokonywania prognoz.

Zawiera `ModelOutput` dwie kolumny:

- `Prediction`: Przewidywana kategoria obrazu.
- `Score`: Lista prawdopodobieństw dla wszystkich kategorii (najwyższa `Prediction`należy do ).

## <a name="troubleshooting"></a>Rozwiązywanie problemów

### <a name="cannot-create-compute"></a>Nie można utworzyć obliczeń

Jeśli wystąpi błąd podczas tworzenia obliczeń usługi Azure Machine Learning, zasób obliczeniowy może nadal istnieć w stanie błędnym. Jeśli spróbujesz ponownie utworzyć zasób obliczeniowy o tej samej nazwie, operacja nie powiedzie się. Aby naprawić ten błąd, albo:

- Tworzenie nowych obliczeń o innej nazwie
- Przejdź do witryny Azure portal i usuń oryginalny zasób obliczeniowy
