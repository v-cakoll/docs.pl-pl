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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="metadata-interfaces"></a>Interfejsy metadanych
W tej sekcji opisano niezarządzane interfejsy, które umożliwiają dostęp do metadanych udostępnianych przez typy .NET Framework, metody, pól i tak dalej.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [ICeeGen, interfejs](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 Udostępnia metody dla kompilacji dynamicznej kodu.  
  
 [IHostFilter, interfejs](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)  
 Zapewnia metodę host czasu wykonywania można oznaczyć tokenów metadanych do przetwarzania.  
  
 [IMapToken, interfejs](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)  
 Zapewnia możliwości mapowania między zaimportowane i wysyłanego podpisów metadanych.  
  
 [IMetaDataAssemblyEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 Udostępnia metody, które obsługują modelu własny opis używany przez środowisko uruchomieniowe języka wspólnego (CLR) do rozwiązania i użycie zasobów.  
  
 [IMetaDataAssemblyImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 Udostępnia metody dostępu i sprawdź zawartość manifest zestawu.  
  
 [IMetaDataConverter, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)  
 Udostępnia metody do mapowania biblioteki typów na ich podpisów metadanych i przekonwertować z jednego do drugiego.  
  
 [IMetaDataDispenser, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 `IMetaDataDispenser` jest przestarzała. Zamiast nich należy używać słów kluczowych `IMetaDataDispenserEx`.  
  
 [IMetaDataDispenserEx, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 Udostępnia metody, które mapują obszary pamięci dla tworzenia lub modyfikowania metadanych.  
  
 [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 Udostępnia metody do tworzenia, modyfikowania i przechowywane metadane dotyczące zestawu w aktualnie określonego zakresu.  
  
 [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 Udostępnia metody służące do definiowania i modyfikowania sygnatur metadanych z parametrami typu metody i konstruktory <xref:System.Type?displayProperty=nameWithType>.  
  
 [IMetaDataError, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)  
 Udostępnia mechanizm wywołania zwrotnego dla usługi raportowania błędów podczas rozpoznawania podpisu metadanych dla zestawu.  
  
 [IMetaDataFilter, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)  
 Udostępnia metody dla oznaczenie i Filtrowanie tokenów metadanych, aby uniknąć powtarzania działania, które zostały już wykonane.  
  
 [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 Udostępnia metody do importowania i manipulowanie typów od innych zestawów.  
  
 [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 Rozszerza `IMetaDataImport` możliwości pracy z typów ogólnych.  
  
 [IMetaDataInfo, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 Udostępnia metody, która pobiera informacje o mapowaniu metadanych z pliku na dysku do pamięci.  
  
 [IMetaDataTables, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 Udostępnia metody przechowywania i pobierania informacji o metadanych w tabelach.  
  
 [IMetaDataTables2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 Rozszerza `IMetaDataTables` uwzględnienie metody pracy ze strumieni metadanych.  
  
 [IMetaDataValidate, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)  
 Udostępnia metody do użycia w celu weryfikacji sygnatury metadanych.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Statyczne funkcje globalne metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)  
  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
  
 [Struktury metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
  
 [Unie metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
