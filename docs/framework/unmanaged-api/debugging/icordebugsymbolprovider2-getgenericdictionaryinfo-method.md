---
title: "ICorDebugSymbolProvider2::GetGenericDictionaryInfo — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63126e4f34ea7ea7dee7dd0b9cae0dc0fea57ed9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a>ICorDebugSymbolProvider2::GetGenericDictionaryInfo — metoda
Pobiera mapy ogólnego słownika.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetGenericDictionaryInfo(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppMemoryBuffer`  
 [out] Wskaźnik do adresu [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) obiektu zawierającego mapy ogólnego słownika. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z platformą .NET Native.  
  
 Mapy składa się z dwóch części najwyższego poziomu:  
  
-   A [katalogu](#Directory) zawierający względnych adresów wirtualnych (RVA) wszystkich słowników uwzględnione na tej mapie.  
  
-   Wyrównane bajtów [sterty](#Heap) zawiera informacje dotyczące tworzenia wystąpienia obiektu. Rozpoczyna się od razu po ostatnim wpisu w katalogu.  
  
<a name="Directory"></a>   
## <a name="the-directory"></a>Katalog  
 Każdy wpis w katalogu, który odwołuje się do przesunięcia w stercie; oznacza to, że jest wartość przesunięcia względem początku sterty. Wartość poszczególne pozycje nie jest zawsze unikatowa. istnieje możliwość wiele wpisów w katalogu wskaż tego samego przesunięcie w stosie.  
  
 Części katalogu mapy słownika ogólnego ma następującą strukturę:  
  
-   Pierwsze 4 bajty zawiera liczbę wpisy słownika (oznacza to, że liczba względną wirtualnych adresów w słowniku). Odnoszą się do tej wartości jako *N*. Jeśli ustawiono bit wysoka, dane są sortowane według wirtualny adres względny w kolejności rosnącej.  
  
-   *N* wykonaj wpisów w katalogu. Każdy wpis zawiera 8 bajtów w dwóch segmentów 4-bajtowych:  
  
    -   Liczba bajtów 0-3: Adres RVA; adres względny wirtualnego słownika.  
  
    -   Bajty 4-7: przesunięcie; przesunięcie względem początku sterty.  
  
<a name="Heap"></a>   
## <a name="the-heap"></a>Sterty  
 Rozmiar sterty można obliczyć przez odjęcie długość strumienia od rozmiaru katalogu + 4 przez czytnik strumienia. Innymi słowy:  
  
```  
Heap Size = Stream.Length – (Directory Size + 4)  
```  
  
 gdzie jest rozmiar katalogu `N * 8`.  
  
 Format dla każdego wystąpienia elementu informacje na stercie jest:  
  
-   Długość tego wystąpienia elementu informacji w bajtach Format skompresowanych metadanych ECMA. Wartość nie obejmuje informacji długości.  
  
-   Liczba typów konkretyzacja rodzajowa lub *T*, format skompresowanych metadanych ECMA.  
  
-   *T* typów, każdy reprezentowany w formacie sygnatury typu ECMA.  
  
 Włączenie długość dla każdego elementu sterty umożliwia proste sortowanie sekcji katalogu bez wpływu na stercie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugSymbolProvider2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
