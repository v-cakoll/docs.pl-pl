---
title: Modelowanie i mapowanie
ms.date: 03/30/2017
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
ms.openlocfilehash: 133539ab1b6d6f2f0ab3f8deed5b22240c2bb07e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854393"
---
# <a name="modeling-and-mapping"></a>Modelowanie i mapowanie
W Entity Framework można zdefiniować model koncepcyjny, model magazynu i mapowanie między nimi w sposób najlepiej pasujący do Twojej aplikacji. Narzędzia Entity Data Model w programie Visual Studio umożliwiają tworzenie. [edmx plik](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)) z bazy danych lub modelu graficznego, a następnie zaktualizuj ten plik, gdy zmieni się baza danych lub model.  
  
 Począwszy od Entity Framework 4,1, można również programistycznie utworzyć model przy użyciu Code First programowanie. Istnieją dwa różne scenariusze tworzenia Code First. W obu przypadkach deweloper definiuje model poprzez kodowanie .NET Framework definicji klas, a następnie opcjonalnie określa dodatkowe mapowanie lub konfigurację przy użyciu adnotacji danych lub interfejsu API Fluent.  
  
 Aby uzyskać więcej informacji, zobacz [Tworzenie i mapowanie modelu koncepcyjnego](https://go.microsoft.com/fwlink/?LinkId=235016).  
  
 Można również użyć generatora EDM, który jest dołączony do .NET Framework. EdmGen. exe generuje pliki CSDL, SSDL i MSL z istniejącego źródła danych. Możesz również ręcznie utworzyć model i zawartość mapowania. Aby uzyskać więcej informacji, zobacz [generator modelu EDM (EdmGen. exe)](edm-generator-edmgen-exe.md).
