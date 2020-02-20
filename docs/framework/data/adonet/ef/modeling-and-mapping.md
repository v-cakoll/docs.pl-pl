---
title: Modelowanie i mapowanie
ms.date: 03/30/2017
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
ms.openlocfilehash: e70411bb9c9797ee348aeef055c9af20ea092ae3
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450599"
---
# <a name="modeling-and-mapping"></a>Modelowanie i mapowanie
W Entity Framework można zdefiniować model koncepcyjny, model magazynu i mapowanie między nimi w sposób najlepiej pasujący do Twojej aplikacji. Narzędzia Entity Data Model w programie Visual Studio umożliwiają tworzenie. [edmx plik](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)) z bazy danych lub modelu graficznego, a następnie zaktualizuj ten plik, gdy zmieni się baza danych lub model.  
  
 Począwszy od Entity Framework 4,1, można również programistycznie utworzyć model przy użyciu Code First programowanie. Istnieją dwa różne scenariusze tworzenia Code First. W obu przypadkach deweloper definiuje model poprzez kodowanie .NET Framework definicji klas, a następnie opcjonalnie określa dodatkowe mapowanie lub konfigurację przy użyciu adnotacji danych lub interfejsu API Fluent.  
  
 Aby uzyskać więcej informacji, zobacz [Tworzenie modelu](/ef/ef6/modeling/).  
  
 Można również użyć generatora EDM, który jest dołączony do .NET Framework. EdmGen. exe generuje pliki CSDL, SSDL i MSL z istniejącego źródła danych. Możesz również ręcznie utworzyć model i zawartość mapowania. Aby uzyskać więcej informacji, zobacz [generator modelu EDM (EdmGen. exe)](edm-generator-edmgen-exe.md).
