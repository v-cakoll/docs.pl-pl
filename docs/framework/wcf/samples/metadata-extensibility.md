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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: abdc2a1cca721450a780f81ff8795fc4e648453f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="metadata-extensibility"></a>Rozszerzalność metadanych
Ta sekcja zawiera przykłady ilustrujące niestandardowych metadanych.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Niestandardowy bezpieczny punkt końcowy metadanych](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)  
 Pokazuje sposób implementacji usługi za pomocą punkt końcowy metadanych bezpiecznego, do którego korzysta z jednego powiązania-metadata exchange oraz sposób konfigurowania [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) lub klientów do pobierania metadanych z taki punkt końcowy metadanych.  
  
 [Niestandardowa publikacja WSDL](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)  
 Pokazuje, jak wdrożyć <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> na niestandardowego <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> atrybutu, aby wyeksportować jako adnotacje WSDL, między innymi funkcji właściwości atrybutów.
