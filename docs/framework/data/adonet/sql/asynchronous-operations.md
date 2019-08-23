---
title: Operacje asynchroniczne
ms.date: 03/30/2017
ms.assetid: e7d32c3c-bf78-4bfc-a357-c9e82e4a4b3c
ms.openlocfilehash: c104176d92667d7c8e2dc83c33bf3eb566437d7f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918126"
---
# <a name="asynchronous-operations"></a>Operacje asynchroniczne
Niektóre operacje bazy danych, takie jak wykonanie polecenia, mogą zająć dużo czasu. W takim przypadku aplikacje jednowątkowe muszą blokować inne operacje i poczekać na zakończenie wykonywania polecenia, zanim będą mogły kontynuować własne operacje. Z kolei możliwość przypisania długotrwałej operacji do wątku w tle umożliwia wątek pierwszego planu pozostanie aktywny w całej operacji. Na przykład w aplikacji systemu Windows delegowanie długotrwałej operacji do wątku w tle pozwala wątku interfejsu użytkownika pozostały czas odpowiedzi podczas wykonywania operacji.  
  
 .NET Framework zawiera kilka standardowych wzorców projektów asynchronicznych, których deweloperzy mogą używać do korzystania z wątków w tle i zwalniania interfejsów użytkownika lub wątków o wysokim priorytecie w celu wykonywania innych operacji. ADO.NET obsługuje te same wzorce projektowe w <xref:System.Data.SqlClient.SqlCommand> swojej klasie. <xref:System.Data.SqlClient.SqlCommand.EndExecuteNonQuery%2A> <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A> <xref:System.Data.SqlClient.SqlCommand.EndExecuteReader%2A> <xref:System.Data.SqlClient.SqlCommand.EndExecuteXmlReader%2A> W szczególnych przypadkach metody <xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A> ,,isąsparowanezmetodami,i,zapewniająobsługęasynchroniczną.<xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>  
  
> [!NOTE]
> Programowanie asynchroniczne jest podstawową funkcją .NET Framework i ADO.NET w pełni wykorzystuje standardowe wzorce projektowe. Aby uzyskać więcej informacji na temat różnych technik asynchronicznych dostępnych dla deweloperów, zobacz [Asynchroniczne wywoływanie metod synchronicznych](../../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
 Chociaż używanie technik asynchronicznych z funkcjami ADO.NET nie dodaje żadnych specjalnych zagadnień, prawdopodobnie więcej deweloperów będzie używać funkcji asynchronicznych w ADO.NET niż w innych obszarach .NET Framework. Ważne jest, aby mieć świadomość korzyści i pułapek tworzenia aplikacji wielowątkowych. Poniższe przykłady w tej sekcji zawierają kilka ważnych problemów, które deweloperzy muszą wziąć pod uwagę podczas kompilowania aplikacji, które zawierają funkcje wielowątkowości.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Aplikacje systemu Windows z wykorzystaniem wywołania zwrotnego](../../../../../docs/framework/data/adonet/sql/windows-applications-using-callbacks.md)  
 Zawiera przykład pokazujący, jak bezpiecznie wykonać polecenie asynchroniczne, prawidłowo obsługiwać interakcję z formularzem i jego zawartością z oddzielnego wątku.  
  
 [Aplikacje ASP.NET z wykorzystaniem uchwytów oczekiwania](../../../../../docs/framework/data/adonet/sql/aspnet-apps-using-wait-handles.md)  
 Zawiera przykład pokazujący sposób wykonywania wielu współbieżnych poleceń na stronie ASP.NET przy użyciu dojść do zajścia do zarządzania operacją po zakończeniu wszystkich poleceń.  
  
 [Sondowanie aplikacji konsoli](../../../../../docs/framework/data/adonet/sql/polling-in-console-applications.md)  
 Przedstawia przykład demonstrujący używanie sondowania, aby oczekiwać na ukończenie asynchronicznego wykonywania poleceń z aplikacji konsolowej. Ta technika jest również prawidłowa w bibliotece klas lub innej aplikacji bez interfejsu użytkownika.  
  
## <a name="see-also"></a>Zobacz także

- [SQL Server i ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [Wywoływanie metod synchronicznych w sposób asynchroniczny](../../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
