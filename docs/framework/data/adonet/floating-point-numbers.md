---
title: Liczby zmiennoprzecinkowe
ms.date: 03/30/2017
ms.assetid: 73c218c6-1c44-4402-a167-4f6262629a91
ms.openlocfilehash: 1f76a6ab8cc2a44580229014dd8ebae6b317921f
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374428"
---
# <a name="floating-point-numbers"></a>Liczby zmiennoprzecinkowe
W tym temacie opisano niektóre problemy, które często napotykają deweloperzy, gdy pracują z liczbą zmiennoprzecinkową w ADO.NET. Te problemy są spowodowane sposobem, w jaki komputery przechowują liczby zmiennoprzecinkowe i nie są specyficzne dla określonego dostawcy, takiego jak <xref:System.Data.SqlClient> lub. <xref:System.Data.OracleClient>  
  
 Liczby zmiennoprzecinkowe zwykle nie mają dokładnej reprezentacji binarnej. Zamiast tego komputer przechowuje przybliżenie liczby. W różnym czasie różne liczby cyfr binarnych mogą być używane do reprezentowania liczby. Gdy liczba zmiennoprzecinkowa jest konwertowana z jednej reprezentacji na inną reprezentację, najmniej znaczące cyfry tej liczby mogą się nieco różnić. Konwersja występuje zwykle, gdy liczba jest rzutowana z jednego typu na inny typ. Odmiana występuje niezależnie od tego, czy konwersja jest wykonywana w bazie danych, między typami reprezentującymi wartości bazy danych, czy między typami. Ze względu na te zmiany liczby, które byłyby logicznie równe, mogą mieć zmiany w ich najmniej znaczących cyfrach, które powodują, że mają różne wartości. Liczba cyfr dokładności w liczbie może być większa lub mniejsza niż oczekiwano. W przypadku formatowania jako ciągu liczba nie może zawierać oczekiwanej wartości.  
  
 Aby zminimalizować te skutki, należy użyć najbliższego dopasowania między typami liczbowymi, które są dla Ciebie dostępne. Na przykład jeśli pracujesz z SQL Server, dokładna wartość liczbowa może ulec zmianie w przypadku konwersji wartości języka Transact-SQL typu rzeczywistego na wartość typu float. W .NET Framework konwersja a <xref:System.Single> na a <xref:System.Double> może również dawać nieoczekiwane wyniki. W obu tych przypadkach dobrą strategią jest upewnienie się, że wszystkie wartości w aplikacji używają tego samego typu liczbowego. Można również użyć typu dziesiętnego o stałej precyzji lub rzutowania liczb zmiennoprzecinkowych na typ dziesiętny o stałej precyzji przed rozpoczęciem pracy z nimi.  
  
 Aby obejść problemy z porównaniem równości, należy rozważyć kodowanie aplikacji tak, aby różnice w najmniej znaczących cyfr zostały zignorowane. Na przykład zamiast porównywania, aby zobaczyć, czy dwie liczby są równe, Odejmij jedną liczbę od drugiej. Jeśli różnica mieści się w akceptowalnym marginesie zaokrąglenia, aplikacja może traktować liczby tak, jakby były takie same.  
  
## <a name="see-also"></a>Zobacz także

- [Dlaczego liczby zmiennoprzecinkowe mogą tracić dokładność](/cpp/build/why-floating-point-numbers-may-lose-precision)
- [Omówienie ADO.NET](ado-net-overview.md)
