---
title: 'Porady: marki, modelu i mapowania plików zasobów osadzonych'
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: 3fd3c3628e94b4727dfc711e02a9f4b754aa8a2c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
 Następujący ciąg połączenia odwołuje się do osadzonego modelu i mapowania plików [modelu sprzedaży AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832). Ten ciąg połączenia jest przechowywany w pliku App.config projektu.  
  
  
  
## <a name="see-also"></a>Zobacz też  
 [Modelowanie i mapowanie](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [Instrukcje: Określanie parametrów połączenia](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)  
 [Instrukcje: Tworzenie ciągu połączenia EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
 [ADO.NET Entity Data Model Tools](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)
