---
title: Interfejsy metadanych
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], metadata
- metadata interfaces [.NET Framework]
- interfaces (.NET Framework metadata]
ms.assetid: f5cdac93-a28c-48ef-8a19-5773376e9e7c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a704d531b1c49ffe653009e0e90f33b7a126e91
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049820"
---
# <a name="metadata-interfaces"></a>Interfejsy metadanych
W tej sekcji opisano niezarządzane interfejsy, które zapewniają dostęp do metadanych udostępnianych przez typów programu .NET Framework, metody, pola i tak dalej.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [ICeeGen, interfejs](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 Udostępnia metody dla kompilacji dynamicznej kodu.  
  
 [IHostFilter, interfejs](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)  
 Zapewnia metodę hosta środowiska wykonawczego oznaczyć tokeny metadanych do przetwarzania.  
  
 [IMapToken, interfejs](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)  
 Zapewnia możliwości mapowania między zaimportowane i emitowane podpisy metadanych.  
  
 [IMetaDataAssemblyEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 Udostępnia metody, które wspierają model własny opis używany przez środowisko uruchomieniowe języka wspólnego (CLR) do rozwiązania i używanie zasobów.  
  
 [IMetaDataAssemblyImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 Udostępnia metody dostępu i sprawdź zawartość w manifeście zestawu.  
  
 [IMetaDataConverter, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)  
 Udostępnia metody, aby zamapować bibliotek typów na ich podpisy metadanych i konwersji z jednego do drugiego.  
  
 [IMetaDataDispenser, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 `IMetaDataDispenser` jest przestarzały. Zamiast nich należy używać słów kluczowych `IMetaDataDispenserEx`.  
  
 [IMetaDataDispenserEx, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 Udostępnia metody, które mapują obszary pamięci dla tworzenia lub modyfikowania metadanych.  
  
 [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 Dostarcza metody do tworzenia, modyfikacji i są przechowywane metadane dotyczące zestawu w aktualnie zdefiniowanego zakresu.  
  
 [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 Zawiera metody służące do definiowania i modyfikowanie metadanych podpisy metod i konstruktorów z parametrami typu <xref:System.Type?displayProperty=nameWithType>.  
  
 [IMetaDataError, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)  
 Udostępnia mechanizm wywołania zwrotnego dla raportowania błędów podczas rozpoznawania podpisu metadanych dla zestawu.  
  
 [IMetaDataFilter, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)  
 Zawiera metody służące do oznaczenia i filtrowanie tokeny metadanych, aby uniknąć powtarzania czynności, które już zostały podjęte.  
  
 [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 Zawiera metody służące do importowania i manipulowanie nimi typów od innych zestawów.  
  
 [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 Rozszerza `IMetaDataImport` możliwości pracy z typów ogólnych.  
  
 [IMetaDataInfo, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 Dostarcza metodę, która pobiera informacje o mapowaniu metadanych z pliku na dysku do pamięci.  
  
 [IMetaDataTables, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 Zawiera metody służące do przechowywania i pobierania informacji o metadanych w tabelach.  
  
 [IMetaDataTables2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 Rozszerza `IMetaDataTables` obejmujący metody do pracy ze strumieniami metadanych.  
  
 [IMetaDataValidate, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)  
 Dostarcza metody do użycia w celu weryfikacji sygnatury metadanych.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Statyczne funkcje globalne metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)  
  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
  
 [Struktury metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
  
 [Unie metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
