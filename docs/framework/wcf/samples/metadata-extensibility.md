---
title: "Rozszerzalność metadanych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f92fcc76-0806-4c84-9d63-7aae0d3899de
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 36eb5940fa1d869948a94fcbbb1945aea1c534ac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="metadata-extensibility"></a>Rozszerzalność metadanych
Ta sekcja zawiera przykłady ilustrujące niestandardowych metadanych.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Niestandardowy bezpieczny punkt końcowy metadanych](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)  
 Pokazuje sposób implementacji usługi za pomocą punkt końcowy metadanych bezpiecznego, do którego korzysta z jednego powiązania-metadata exchange oraz sposób konfigurowania [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) lub klientów do pobierania metadanych z taki punkt końcowy metadanych.  
  
 [Niestandardowa publikacja WSDL](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)  
 Pokazuje, jak wdrożyć <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> na niestandardowego <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> atrybutu, aby wyeksportować jako adnotacje WSDL, między innymi funkcji właściwości atrybutów.
