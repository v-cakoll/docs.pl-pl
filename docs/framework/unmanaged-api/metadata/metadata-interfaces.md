---
title: Interfejsy metadanych
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], metadata
- metadata interfaces [.NET Framework]
- interfaces (.NET Framework metadata]
ms.assetid: f5cdac93-a28c-48ef-8a19-5773376e9e7c
ms.openlocfilehash: 4672cb813cec4a127f7888a2273eb26c3f34c3d9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431591"
---
# <a name="metadata-interfaces"></a>Interfejsy metadanych
W tej sekcji opisano niezarządzane interfejsy, które zapewniają dostęp do metadanych uwidocznionych przez typy .NET Framework, metody, pola itd.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [ICeeGen, interfejs](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 Zapewnia metody dynamicznego kompilowania kodu.  
  
 [IHostFilter, interfejs](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)  
 Zapewnia metodę dla hosta czasu wykonywania, aby oznaczyć tokeny metadanych do przetwarzania.  
  
 [IMapToken, interfejs](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)  
 Oferuje możliwości mapowania między zaimportowanymi i emitowanymi sygnaturami metadanych.  
  
 [IMetaDataAssemblyEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 Dostarcza metody, które obsługują model z własnymi opisami używany przez środowisko uruchomieniowe języka wspólnego (CLR) do rozwiązywania i korzystania z zasobów.  
  
 [IMetaDataAssemblyImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 Zapewnia metody umożliwiające dostęp i sprawdzanie zawartości manifestu zestawu.  
  
 [IMetaDataConverter, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)  
 Zapewnia metody mapowania bibliotek typów na ich sygnatury metadanych oraz do konwersji między nimi.  
  
 [IMetaDataDispenser, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 `IMetaDataDispenser` jest przestarzała. Zamiast nich należy używać słów kluczowych `IMetaDataDispenserEx`.  
  
 [IMetaDataDispenserEx, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 Dostarcza metody, które mapują obszary pamięci do tworzenia lub modyfikowania metadanych.  
  
 [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 Zapewnia metody tworzenia, modyfikowania i przechowywania metadanych dotyczących zestawu w aktualnie zdefiniowanym zakresie.  
  
 [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 Zapewnia metody definiowania i modyfikowania sygnatur metadanych metod i konstruktorów z parametrami typu <xref:System.Type?displayProperty=nameWithType>.  
  
 [IMetaDataError, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)  
 Zapewnia mechanizm wywołania zwrotnego do raportowania błędów podczas rozpoznawania podpisu metadanych dla zestawu.  
  
 [IMetaDataFilter, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)  
 Zapewnia metody oznaczania i filtrowania tokenów metadanych, aby uniknąć powtarzających się akcji, które zostały już wykonane.  
  
 [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 Zapewnia metody importowania typów z innych zestawów i manipulowania nimi.  
  
 [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 Rozszerza `IMetaDataImport`, aby zapewnić możliwość pracy z typami ogólnymi.  
  
 [IMetaDataInfo, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 Zapewnia metodę, która pobiera informacje o mapowaniu metadanych z pliku na dysku do pamięci.  
  
 [IMetaDataTables, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 Zapewnia metody przechowywania i pobierania informacji o metadanych w tabelach.  
  
 [IMetaDataTables2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 Rozszerza `IMetaDataTables`, aby uwzględnić metody pracy z strumieniami metadanych.  
  
 [IMetaDataValidate, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)  
 Zapewnia metody do użycia w celu walidacji sygnatur metadanych.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Statyczne funkcje globalne metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)  
  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
  
 [Struktury metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
  
 [Unie metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
