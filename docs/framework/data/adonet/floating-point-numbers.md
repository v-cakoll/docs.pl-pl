---
title: Liczby zmiennoprzecinkowe
ms.date: 03/30/2017
ms.assetid: 73c218c6-1c44-4402-a167-4f6262629a91
ms.openlocfilehash: aae7bd2ea6b5ba7bc9c69b99c93b62ba7a413d59
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102521"
---
# <a name="floating-point-numbers"></a>Liczby zmiennoprzecinkowe
W tym temacie opisano niektóre problemy, które często deweloperzy napotykają podczas pracy z liczb zmiennoprzecinkowych w [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. Te problemy są spowodowane przez sposób komputerom przechowywania liczb zmiennoprzecinkowych i nie są specyficzne dla określonego dostawcy takich jak <xref:System.Data.SqlClient> lub <xref:System.Data.OracleClient>.  
  
 Liczby zmiennoprzecinkowe zwykle nie mają dokładnie reprezentacja binarna. Zamiast tego komputer przechowuje przybliżeniem liczby. W różnym czasie różną liczbę cyfr, może służyć do reprezentowania liczby. Gdy zmiennoprzecinkowy punktu, że liczba jest konwertowana z reprezentacji jednego innego reprezentacji najmniej znaczącymi cyframi tej liczby może się nieco różnić. Konwersja zazwyczaj występuje, gdy liczba jest rzutowanie z jednego typu na inny typ. Zmiana występuje, czy konwersja występuje w bazie danych, między typami, które reprezentują wartości z bazy danych lub między typami. Z powodu tych zmian numery, które logicznie są takie same może mieć zmian w ich najmniej znaczący cyfr, które spowoduje ich mają różne wartości. Liczba cyfr w numerze może być większy lub mniejszy niż oczekiwano. Gdy sformatowany jako ciąg, liczba nie mogą być wyświetlane z oczekiwaną wartością.  
  
 Aby zminimalizować te skutki, należy użyć najlepiej dopasowany między typy liczbowe, które są dostępne dla Ciebie. Na przykład jeśli pracujesz z programem SQL Server, dokładna wartość numeryczna może zmienić wartość rzeczywistego typu języka Transact-SQL po konwersji na wartość typu float. W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], konwertowania <xref:System.Single> do <xref:System.Double> także może powodować nieoczekiwane rezultaty. W obu przypadkach dobre rozwiązanie jest wszystkie wartości w aplikacji użyj tego samego typu liczbowego. Można również użyć typu dziesiętnego dokładności stałej lub Rzutowanie liczb zmiennoprzecinkowych do typu dziesiętnego stałej dokładności, przed rozpoczęciem pracy z nimi.  
  
 Aby uniknąć problemów z funkcją porównania równości, należy wziąć pod uwagę kodowania aplikacji, tak aby zmiany w najmniej znaczącymi cyframi są ignorowane. Na przykład zamiast porównywania, aby zobaczyć, czy dwie liczby są równe, Odejmij jedną cyfrę z drugiej liczby. Jeśli różnica jest dopuszczalne marginesem zaokrąglania, aplikację można traktować liczb, tak, jakby były takie same.  
  
## <a name="see-also"></a>Zobacz także

- [Dlaczego liczby zmiennoprzecinkowe mogą tracić dokładność](/cpp/build/reference/why-floating-point-numbers-may-lose-precision)
- [Omówienie ADO.NET](ado-net-overview.md)
