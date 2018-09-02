---
title: Operacje asynchroniczne
ms.date: 03/30/2017
ms.assetid: e7d32c3c-bf78-4bfc-a357-c9e82e4a4b3c
ms.openlocfilehash: c1c99437ada9dd9e71e0e999073e8d207569c2bf
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463081"
---
# <a name="asynchronous-operations"></a>Operacje asynchroniczne
Niektóre operacje bazy danych, takich jak wykonania polecenia może potrwać znaczną ilość czasu, aby zakończyć. W takim przypadku aplikacje jednowątkowe należy blokuje to innych operacji i czekać na zakończenie przed kontynuowaniem pracy ich własnych operacji polecenia. Możliwość przypisywania długotrwałej operacji do wątku w tle z kolei umożliwia wątku na pierwszym planie, pozostaną aktywne podczas operacji. W aplikacji Windows na przykład delegowanie długotrwałej operacji w wątku tła umożliwia wątek interfejsu użytkownika nadal odpowiadać podczas wykonywania operacji.  
  
 .NET Framework zapewnia kilka standardowych asynchroniczne wzorce projektowe, które umożliwia programistom korzystanie z zalet wątków w tle i bezpłatne interfejsu użytkownika lub o wysokim priorytecie wątków do wykonania innych operacji. ADO.NET obsługuje te sam wzorce projektowe w jego <xref:System.Data.SqlClient.SqlCommand> klasy. W szczególności <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, <xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A>, i <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A> metod, w połączeniu z <xref:System.Data.SqlClient.SqlCommand.EndExecuteNonQuery%2A>, <xref:System.Data.SqlClient.SqlCommand.EndExecuteReader%2A>, i <xref:System.Data.SqlClient.SqlCommand.EndExecuteXmlReader%2A> metod, zapewnienie asynchronicznej obsługi.  
  
> [!NOTE]
>  Programowanie asynchroniczne jest podstawowych funkcji programu .NET Framework i ADO.NET wykorzystuje pełną standardowe wzorce projektowe. Aby uzyskać więcej informacji na temat różnych technik asynchronicznego, dostępna dla deweloperów, zobacz [wywołanie asynchroniczne synchroniczne metody](../../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
 Mimo że używanie metod asynchronicznych za pomocą narzędzia ADO.NET funkcji nie powoduje dodania uwagi użytkownika, istnieje prawdopodobieństwo, że więcej umożliwia deweloperom funkcje asynchroniczne w ADO.NET niż w innych obszarach programu .NET Framework. Należy mieć świadomość korzyści i pułapek tworzenia aplikacji wielowątkowych. Przykłady, które należy wykonać w tej sekcji wskazują kilka ważnych problemów tego deweloperów należy wziąć pod uwagę podczas tworzenia aplikacji, obejmujące funkcje wielowątkowych.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Aplikacje systemu Windows z wykorzystaniem wywołania zwrotnego](../../../../../docs/framework/data/adonet/sql/windows-applications-using-callbacks.md)  
 Przykład pokazująca, jak bezpiecznie, wykonanie polecenia asynchronicznego poprawnie obsługi interakcji z formularza i jego zawartość w oddzielnym wątku.  
  
 [Aplikacje ASP.NET z wykorzystaniem uchwytów oczekiwania](../../../../../docs/framework/data/adonet/sql/aspnet-apps-using-wait-handles.md)  
 Przykład ukazujące sposób wykonywać wiele równoczesnych polecenia ze strony programu ASP.NET, przy użyciu dojścia oczekiwania zarządzać działaniem na zakończenie wszystkich poleceń.  
  
 [Sondowanie aplikacji konsoli](../../../../../docs/framework/data/adonet/sql/polling-in-console-applications.md)  
 Przykład ilustrujące użycie sondowania czekać na zakończenie wykonywania polecenia asynchronicznego z aplikacji konsoli. Ta technika jest również prawidłowe w bibliotece klas lub innych aplikacji bez interfejsu użytkownika.  
  
## <a name="see-also"></a>Zobacz też  
 [SQL Server i ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [Wywoływanie metod synchronicznych w sposób asynchroniczny](../../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
