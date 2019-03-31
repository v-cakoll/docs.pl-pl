---
title: Manifest zestawu
ms.date: 03/30/2017
helpviewer_keywords:
- assembly manifest
- dynamic assemblies, assembly manifest
- metadata, assembly manifest
- culture, assembly manifest
- assemblies [.NET Framework], metadata
ms.assetid: 8e40fab9-549d-4731-aec2-ffa47a382de0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8acf811b835d5afd8686701fe269b16d4b766458
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2019
ms.locfileid: "58676072"
---
# <a name="assembly-manifest"></a>Manifest zestawu
Każdy zestaw statyczny i dynamiczny zawiera kolekcję danych, które opisują powiązania między elementami zawartymi w zestawie. Manifest zestawu zawiera metadane zestawu. W manifeście zestawu znajdują się wszystkie metadane potrzebne do określenia wymagań w zakresie wersji zestawu i tożsamości jego zabezpieczeń, a także wszystkie metadane niezbędne do definiowania zakresu zestawu oraz rozpoznawania odwołań do zasobów i klas. Manifest zestawu może być przechowywany w pliku PE (.exe lub .dll) mającym kod w języku Microsoft Intermediate Language (MSIL) lub w samodzielnym pliku PE, który zawiera tylko dane manifestu zestawu.  
  
 Na ilustracji poniżej widać różne sposoby przechowywania manifestu.  
  
 ![Diagram przedstawiający manifest w zestawu pojedynczego pliku i zestawu wieloplikowego konfiguracji.](./media/assembly-manifest/assembly-types-diagram.gif)  
  
 Dla zestawu o jednym skojarzonym pliku manifest jest umieszczony w pliku PE, co tworzy zestaw jednoplikowy. Zestaw wieloplikowy może zawierać autonomiczny plik manifestu lub manifest umieszczony w jednym z plików PE w zestawie.  
  
 Manifest każdego zestawu wykonuje następujące funkcje:  
  
-   Wylicza pliki tworzące zestaw.  
  
-   Określa, w jaki sposób odwołania do typów i zasobów zestawów są mapowane na pliki zawierające ich deklaracje i implementacje.  
  
-   Wylicza inne zestawy, od których zależy zestaw.  
  
-   Tworzy poziom pośredni między obiektami używającymi zestawu a szczegółami implementacji zestawu.  
  
-   Sprawia, że zestaw sam siebie opisuje.  
  
## <a name="assembly-manifest-contents"></a>Zawartość manifestu zestawu  
 Poniższa tabela pokazuje informacje zawarte w manifeście zestawu. Pierwsze cztery elementy — nazwa zestawu, numer wersji, kultura i informacje o silnej nazwie — tworzą tożsamość zestawu.  
  
|Informacje|Opis|  
|-----------------|-----------------|  
|Nazwa zestawu|Ciąg tekstowy określający nazwę zestawu.|  
|Numer wersji|Główny i pomocniczy numer wersji oraz numery poprawki i kompilacji. Na podstawie tych numerów środowisko uruchomieniowe języka wspólnego wymusza zasady dotyczące wersji.|  
|Kultura|Informacje o kulturze lub języku obsługiwanym przez zestaw. Informacji tych należy używać wyłącznie w celu oznaczenia zestawu jako zestawu satelickiego zawierającego informacje specyficzne dla kultury lub języka. (Zestaw z informacjami o kulturze jest automatycznie traktowany jako satelicki).|  
|Informacje o silnej nazwie|Klucz publiczny od wydawcy, jeśli zestawowi nadano silną nazwę.|  
|Lista wszystkich plików w zestawie|Skrót utworzony na podstawie zawartości każdego pliku w zestawie i nazwy pliku. Wszystkie pliki tworzące zestaw muszą być w tym samym katalogu co plik zawierający manifest zestawu.|  
|Informacje o odwołaniu do typu|Informacje, na podstawie których środowisko uruchomieniowe mapuje odwołanie do typu na plik zawierający jego deklarację i implementację. Wykorzystywane do typów eksportowanych z zestawu.|  
|Informacje o przywoływanych zestawach|Lista innych zestawów, do których prowadzą statyczne odwołania z zestawu. Każde odwołanie zawiera nazwę zależnego zestawu, metadane zestawu (wersja, kultura, system operacyjny itd.) oraz klucz publiczny, jeśli zestaw ma silną nazwę.|  
  
 Niektóre informacje w manifeście zestawu można dodawać i zmieniać w kodzie za pomocą atrybutów zestawu. M.in. można zmienić informacje o wersji i atrybuty informacyjne, w tym dotyczące znaku towarowego, praw autorskich, produktu, firmy i danych informacyjnych wersji. Aby uzyskać pełną listę atrybutów zestawu, zobacz [Konfigurowanie atrybutów zestawu](../../../docs/framework/app-domains/set-assembly-attributes.md).  
  
## <a name="see-also"></a>Zobacz także
- [Zawartość zestawu](../../../docs/framework/app-domains/assembly-contents.md)
- [Przechowywanie wersji zestawu](../../../docs/framework/app-domains/assembly-versioning.md)
- [Tworzenie zestawów satelickich](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [Zestawy o silnych nazwach](../../../docs/framework/app-domains/strong-named-assemblies.md)
