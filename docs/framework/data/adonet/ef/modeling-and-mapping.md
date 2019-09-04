---
title: Modelowanie i mapowanie
ms.date: 03/30/2017
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
ms.openlocfilehash: 33064d35b7ac4c469df3ca6f0111cc84ef10eb08
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248498"
---
# <a name="modeling-and-mapping"></a>Modelowanie i mapowanie
[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]W programie można zdefiniować model koncepcyjny, model magazynu oraz mapowanie między nimi w sposób najlepiej pasujący do Twojej aplikacji. Narzędzia Entity Data Model w programie Visual Studio umożliwiają tworzenie. [edmx plik](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)) z bazy danych lub modelu graficznego, a następnie zaktualizuj ten plik, gdy zmieni się baza danych lub model.  
  
 Począwszy od Entity Framework 4,1, można również programistycznie utworzyć model przy użyciu Code First programowanie. Istnieją dwa różne scenariusze tworzenia Code First. W obu przypadkach deweloper definiuje model poprzez kodowanie .NET Framework definicji klas, a następnie opcjonalnie określa dodatkowe mapowanie lub konfigurację przy użyciu adnotacji danych lub interfejsu API Fluent.  
  
 Aby uzyskać więcej informacji, zobacz [Tworzenie i mapowanie modelu koncepcyjnego](https://go.microsoft.com/fwlink/?LinkId=235016).  
  
 Można również użyć generatora EDM, który jest dołączony do .NET Framework. EdmGen. exe generuje pliki CSDL, SSDL i MSL z istniejącego źródła danych. Możesz również ręcznie utworzyć model i zawartość mapowania. Aby uzyskać więcej informacji, zobacz [generator modelu EDM (EdmGen. exe)](edm-generator-edmgen-exe.md).
