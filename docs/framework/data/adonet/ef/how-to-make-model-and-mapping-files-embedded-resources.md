---
title: "Porady: marki, modelu i mapowania plików zasobów osadzonych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 98fb3ada369279a34ed08110644aabcbbe72a501
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a>Porady: marki, modelu i mapowania plików zasobów osadzonych
[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Umożliwia wdrażanie modeli i mapowania plików jako zasoby osadzone w aplikacji. W tej samej domenie aplikacji połączeniem jednostki musi można załadować zestawu z osadzonego modelu i mapowania plików. Aby uzyskać więcej informacji, zobacz [parametry połączenia](../../../../../docs/framework/data/adonet/ef/connection-strings.md). Domyślnie [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] narzędzia osadzić modelu i mapowania plików. Podczas definiowania ręcznie modelu i mapowania plików, użyj tej procedury, aby upewnić się, że pliki są wdrażane jako zasoby osadzone razem z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikacji.  
  
> [!NOTE]
>  Aby zachować zasoby osadzone, należy powtórzyć całą procedurę modyfikacjach modelu i mapowania plików.  
  
### <a name="to-embed-model-and-mapping-files"></a>Aby osadzić modelu i mapowania plików  
  
1.  W **Eksploratora rozwiązań**, wybierz plik koncepcyjny (CSDL).  
  
2.  W **właściwości** ustawić okienku **Akcja kompilacji** do **osadzonego zasobu**.  
  
3.  Powtórz kroki 1 i 2 dla pliku magazynu (ssdl) i pliku mapowania (MSL).  
  
4.  W **Eksploratora rozwiązań**, kliknij dwukrotnie plik App.config, a następnie zmodyfikuj `Metadata` parametru w `connectionString` atrybutu na podstawie jednej z następujących formatów:  
  
    -   `Metadata=``res://<assemblyFullName>/<resourceName>;`  
  
    -   `Metadata=``res://*/<resourceName>;`  
  
    -   `Metadata=res://*;`  
  
     Aby uzyskać więcej informacji, zobacz [parametry połączenia](../../../../../docs/framework/data/adonet/ef/connection-strings.md).  
  
## <a name="example"></a>Przykład  
 Następujący ciąg połączenia odwołuje się do osadzonego modelu i mapowania plików [modelu sprzedaży AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832). Ten ciąg połączenia jest przechowywany w pliku App.config projektu.  
  
  
  
## <a name="see-also"></a>Zobacz też  
 [Mapowanie i modelowania](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [Porady: Definiowanie parametrów połączenia](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)  
 [Porady: Tworzenie ciągu połączenia EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
 [ADO.NET Entity Data Model Tools](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)
