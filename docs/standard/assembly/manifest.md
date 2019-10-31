---
title: Manifest zestawu
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest
- dynamic assemblies, assembly manifest
- metadata, assembly manifest
- culture, assembly manifest
- assemblies [.NET Framework], metadata
ms.assetid: 8e40fab9-549d-4731-aec2-ffa47a382de0
ms.openlocfilehash: f1913f8c41ba4a7b54f7abcdfb97400503da8ac5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107151"
---
# <a name="assembly-manifest"></a>Manifest zestawu
Każdy zestaw statyczny i dynamiczny zawiera kolekcję danych, które opisują powiązania między elementami zawartymi w zestawie. Manifest zestawu zawiera metadane zestawu. W manifeście zestawu znajdują się wszystkie metadane potrzebne do określenia wymagań w zakresie wersji zestawu i tożsamości jego zabezpieczeń, a także wszystkie metadane niezbędne do definiowania zakresu zestawu oraz rozpoznawania odwołań do zasobów i klas. Manifest zestawu może być przechowywany w pliku PE ( *exe* lub *. dll*) przy użyciu kodu języka pośredniego (MSIL) firmy Microsoft lub w autonomicznym pliku PE, który zawiera tylko informacje manifestu zestawu.  
  
 Na ilustracji poniżej widać różne sposoby przechowywania manifestu.  
  
 ![Diagram przedstawiający manifest w zestawie jednoplikowym i wieloplikowym konfiguracji zestawu.](./media/manifest/assembly-types-diagram.gif)  
  
 Dla zestawu o jednym skojarzonym pliku manifest jest umieszczony w pliku PE, co tworzy zestaw jednoplikowy. Zestaw wieloplikowy może zawierać autonomiczny plik manifestu lub manifest umieszczony w jednym z plików PE w zestawie.  
  
 Manifest każdego zestawu wykonuje następujące funkcje:  
  
- Wylicza pliki tworzące zestaw.  
  
- Określa, w jaki sposób odwołania do typów i zasobów zestawów są mapowane na pliki zawierające ich deklaracje i implementacje.  
  
- Wylicza inne zestawy, od których zależy zestaw.  
  
- Tworzy poziom pośredni między obiektami używającymi zestawu a szczegółami implementacji zestawu.  
  
- Sprawia, że zestaw sam siebie opisuje.  
  
## <a name="assembly-manifest-contents"></a>Zawartość manifestu zestawu  
 Poniższa tabela pokazuje informacje zawarte w manifeście zestawu. Pierwsze cztery elementy: Nazwa zestawu, numer wersji, kultura i informacje o silnej nazwie składają się na tożsamość zestawu.  
  
|Informacje|Opis|  
|-----------------|-----------------|  
|Nazwa zestawu|Ciąg tekstowy określający nazwę zestawu.|  
|Numer wersji|Główny i pomocniczy numer wersji oraz numery poprawki i kompilacji. Na podstawie tych numerów środowisko uruchomieniowe języka wspólnego wymusza zasady dotyczące wersji.|  
|dziedzinie|Informacje o kulturze lub języku obsługiwanym przez zestaw. Informacji tych należy używać wyłącznie w celu oznaczenia zestawu jako zestawu satelickiego zawierającego informacje specyficzne dla kultury lub języka. (Zestaw z informacjami o kulturze jest automatycznie traktowany jako satelicki).|  
|Informacje o silnej nazwie|Klucz publiczny od wydawcy, jeśli zestawowi nadano silną nazwę.|  
|Lista wszystkich plików w zestawie|Skrót utworzony na podstawie zawartości każdego pliku w zestawie i nazwy pliku. Wszystkie pliki tworzące zestaw muszą być w tym samym katalogu co plik zawierający manifest zestawu.|  
|Informacje o odwołaniu do typu|Informacje, na podstawie których środowisko uruchomieniowe mapuje odwołanie do typu na plik zawierający jego deklarację i implementację. Wykorzystywane do typów eksportowanych z zestawu.|  
|Informacje o przywoływanych zestawach|Lista innych zestawów, do których prowadzą statyczne odwołania z zestawu. Każde odwołanie zawiera nazwę zależnego zestawu, metadane zestawu (wersja, kultura, system operacyjny itd.) oraz klucz publiczny, jeśli zestaw ma silną nazwę.|  
  
 Niektóre informacje w manifeście zestawu można dodawać i zmieniać w kodzie za pomocą atrybutów zestawu. M.in. można zmienić informacje o wersji i atrybuty informacyjne, w tym dotyczące znaku towarowego, praw autorskich, produktu, firmy i danych informacyjnych wersji. Aby uzyskać pełną listę atrybutów zestawu, zobacz [Ustawianie atrybutów zestawu](set-attributes.md).  
  
## <a name="see-also"></a>Zobacz także

- [Zawartość zestawu](contents.md)
- [Przechowywanie wersji zestawu](versioning.md)
- [Tworzenie zestawów satelickich](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [Zestawy o silnych nazwach](strong-named.md)
