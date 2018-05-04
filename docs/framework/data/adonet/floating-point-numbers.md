---
title: Liczby zmiennoprzecinkowe
ms.date: 03/30/2017
ms.assetid: 73c218c6-1c44-4402-a167-4f6262629a91
ms.openlocfilehash: b9a3daf68dc8d83727dd7def5251ecb3092dc752
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="floating-point-numbers"></a>Liczby zmiennoprzecinkowe
W tym temacie opisano niektóre problemy napotykane przez programistów często podczas pracy z liczb zmiennoprzecinkowych w [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. Te problemy są powodowane przez sposób przechowywania liczb zmiennoprzecinkowych komputerów i nie są specyficzne dla określonego dostawcy takich jak <xref:System.Data.SqlClient> lub <xref:System.Data.OracleClient>.  
  
 Liczby zmiennoprzecinkowe nie mają zwykle dokładne reprezentacja binarna. Zamiast tego komputer przechowuje przybliżenie liczby. W różnym czasie różną liczbę cyfr może być używany do reprezentowania numer. Gdy zmiennoprzecinkową punktu się, że liczba jest konwertowana z reprezentacji jednego innego reprezentacji co najmniej cyfr znaczących tego numeru mogą się nieco różnić. Konwersja zwykle występuje, gdy liczba jest rzutowane z jednego typu do innego typu. Zmiana występuje, czy konwersja występuje w bazie danych między typów, które reprezentują wartości bazy danych lub typów. Ze względu na te zmiany numery, które logicznie są takie same może mieć zmian w ich najmniej znaczący cyfr, które spowodować mają różne wartości. Liczba cyfr precyzji numer może być większy lub mniejszy niż oczekiwano. Sformatowany jako ciąg, liczbę mogą nie pokazywać oczekiwanej wartości.  
  
 Aby zminimalizować tych skutków, należy użyć najbliższa między typy liczbowe, które są dostępne. Na przykład podczas pracy z programem SQL Server, dokładną wartość liczbową może zmienić języka Transact-SQL wartość rzeczywistą po konwersji na wartości typu float. W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], konwertowania <xref:System.Single> do <xref:System.Double> również może dać nieoczekiwane wyniki. W obu przypadkach dobre rozwiązanie jest zapewnienie wszystkich wartości w przypadku użycia aplikacji tego samego typu liczbowego. Można również używać typu decimal dokładności stałej lub Rzutowanie liczb zmiennoprzecinkowych do typu decimal stałej dokładności przed rozpoczęciem pracy z nimi.  
  
 Aby uniknąć problemów z porównania równości, należy wziąć pod uwagę kodowania aplikacji, tak aby zmiany w co najmniej cyfr znaczących są ignorowane. Na przykład zamiast porównanie, aby zobaczyć, czy dwie liczb są takie same, odjąć jedną liczbę od innych. Jeśli różnica mieści się w dopuszczalnych margines zaokrąglania, aplikację można traktować liczby tak, jakby były takie same.  
  
## <a name="see-also"></a>Zobacz też  
 [Dlaczego liczby zmiennoprzecinkowe mogą tracić dokładność](http://msdn.microsoft.com/library/1acb1add-ac06-4134-a2fd-aff13d8c4c15)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
