---
title: Model Builder — zasoby szkoleniowe platformy Azure
description: Przewodnik po zasobach dla Azure Machine Learning
ms.topic: reference
ms.date: 02/27/2020
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: 866fd5a90d13f85f2f8a1aa45ff0e1efb0096642
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159302"
---
# <a name="model-builder-azure-training-resources"></a>Model Builder — zasoby szkoleniowe platformy Azure

Poniżej przedstawiono przewodnik, który pomoże Ci dowiedzieć się więcej o zasobach używanych do uczenia modeli na platformie Azure przy użyciu konstruktora modeli.

## <a name="what-is-an-azure-machine-learning-experiment"></a>Co to jest Azure Machine Learning eksperyment?

Azure Machine Learning eksperyment jest zasobem, który należy utworzyć przed uruchomieniem szkolenia programu model Builder na platformie Azure.

Eksperyment hermetyzuje konfigurację i wyniki dla co najmniej jednego przebiegu szkoleniowego uczenia maszynowego. Eksperymenty należą do określonego obszaru roboczego. Podczas pierwszego tworzenia eksperymentu jego nazwa jest rejestrowana w obszarze roboczym. Wszystkie kolejne uruchomienia — Jeśli używana jest ta sama nazwa eksperymentu — są rejestrowane jako część tego samego eksperymentu. W przeciwnym razie zostanie utworzony nowy eksperyment.

## <a name="what-is-an-azure-machine-learning-workspace"></a>Co to jest obszar roboczy Azure Machine Learning?

Obszar roboczy jest zasobem Azure Machine Learning, który oferuje centralne miejsce dla wszystkich zasobów Azure Machine Learning i artefaktów utworzonych w ramach przebiegu szkoleniowego.

Aby utworzyć obszar roboczy Azure Machine Learning, wymagane są następujące elementy:

- Nazwa: Nazwa obszaru roboczego od 3-33 znaków. Nazwy mogą zawierać tylko znaki alfanumeryczne i łączniki. 
- Region: Lokalizacja geograficzna centrum danych, w którym są wdrażane obszary robocze i zasoby. Zalecane jest, aby wybrać lokalizację, w której znajdują się użytkownicy lub klienci.
- Grupa zasobów: kontener zawierający wszystkie powiązane zasoby dla rozwiązania platformy Azure.

## <a name="what-is-an-azure-machine-learning-compute"></a>Co to jest Azure Machine Learning COMPUTE?

Azure Machine Learning COMPUTE to oparta na chmurze maszyna wirtualna z systemem Linux służąca do uczenia się.

Aby utworzyć obszar roboczy Azure Machine Learning, wymagane są następujące elementy:

- Nazwa: Nazwa obszaru roboczego od 2-16 znaków. Nazwy mogą zawierać tylko znaki alfanumeryczne i łączniki.
- Rozmiar obliczeń

    Konstruktor modelu może korzystać z jednego z następujących typów obliczeń zoptymalizowanych pod kątem procesora GPU:

    | Rozmiar | Procesor wirtualny | Pamięć: GiB | Magazyn tymczasowy (SSD): GiB | Procesory GPU | Pamięć procesora GPU: GiB | Maks. liczba dysków danych | Maksymalna liczba kart sieciowych |
    |---|---|---|---|---|---|---|---|
    | Standardowa_NC12   | 12 | 112 | 680  | 2 | 24 | 48 | 2 |
    | Standardowa_NC24   | 24 | 224 | 1440 | 4 | 48 | 64 | 4 |

    Zapoznaj się z [dokumentacją maszyn wirtualnych z systemem Linux z serii NC](https://docs.microsoft.com/azure/virtual-machines/nc-series?toc=/azure/virtual-machines/linux/toc.json&bc=/azure/virtual-machines/linux/breadcrumb/toc.json) , aby uzyskać więcej informacji na temat typów obliczeń zoptymalizowanych według procesora GPU

## <a name="training"></a>Szkolenia

Szkolenie na platformie Azure jest dostępne tylko dla scenariusza klasyfikacji obrazu konstruktora modeli. Algorytm używany do uczenia tych modeli jest głębokiej sieci neuronowych na podstawie architektury ResNet50. Proces uczenia zajmuje trochę czasu, a ilość czasu może się różnić w zależności od rozmiaru wybranych obliczeń oraz ilości danych. Przy pierwszym szkoleniu modelu można oczekiwać nieco dłuższego czasu uczenia się, ponieważ zasoby muszą być inicjowane. Postęp przebiegów można śledzić, wybierając link "Monitoruj bieżące uruchomienia w Azure Portal" w programie Visual Studio.

## <a name="results"></a>Wyniki

Po zakończeniu szkolenia dwa projekty są dodawane do rozwiązania przy użyciu następujących sufiksów:

- *ConsoleApp*: aplikacja C# konsolowa platformy .NET Core, która udostępnia kod początkowy do kompilowania potoku predykcyjnego i tworzenia prognoz.
- *Model*: aplikacja C# .NET Standard, która zawiera modele danych, które definiują schemat danych wejściowych i wyjściowych modelu oraz następujące zasoby:

  - bestModel. Onnx: serializowana wersja modelu w formacie Open neuronowych Network Exchange (ONNX). ONNX to format typu open source dla modeli AI, który obsługuje współdziałanie między strukturami, takimi jak ML.NET, PyTorch i TensorFlow.
  - bestModelMap. JSON: Lista kategorii używanych podczas prognozowania w celu mapowania danych wyjściowych modelu do kategorii tekstu.
  - MLModel. zip: szeregowana wersja potoku prognozowania ML.NET, która używa serializowanej wersji modelu *bestModel. Onnx* , aby tworzyć prognozy i mapy dane wyjściowe przy użyciu pliku `bestModelMap.json`.

## <a name="use-the-machine-learning-model"></a>Korzystanie z modelu uczenia maszynowego

Klasy `ModelInput` i `ModelOutput` w projekcie *modelu* definiują odpowiednio dane wejściowe i wyjściowe modelu.

W scenariuszu klasyfikacji obrazu `ModelInput` zawiera dwie kolumny:

- `ImageSource`: ścieżka ciągu lokalizacji obrazu.
- `Label`: rzeczywista Kategoria, do której należy obraz. `Label` jest używany tylko jako dane wejściowe w przypadku szkolenia i nie muszą być dostarczane podczas tworzenia prognoz.

`ModelOutput` zawiera dwie kolumny:

- `Prediction`: prognozowana Kategoria obrazu.
- `Score`: Lista prawdopodobieństwa dla wszystkich kategorii (najwyższa należy do `Prediction`).

## <a name="troubleshooting"></a>Rozwiązywanie problemów

### <a name="cannot-create-compute"></a>Nie można utworzyć obliczeń

Jeśli wystąpi błąd podczas tworzenia Azure Machine Learning obliczeń, zasób obliczeniowy może nadal istnieć w stanie błędu. Jeśli spróbujesz ponownie utworzyć zasób obliczeniowy o tej samej nazwie, operacja zakończy się niepowodzeniem. Aby naprawić ten błąd, należy:

- Utwórz nowe obliczenie przy użyciu innej nazwy
- Przejdź do Azure Portal i Usuń oryginalny zasób obliczeniowy
