---
title: Metoda ICorDebugSymbolProvider2::GetGenericDictionaryInfo
ms.date: 03/30/2017
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5696dc8fcf4b5c84e12ca60f93679f7b67d5f7e9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476324"
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a>Metoda ICorDebugSymbolProvider2::GetGenericDictionaryInfo
Pobiera mapę generyczny słownik.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetGenericDictionaryInfo(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppMemoryBuffer`  
 [out] Wskaźnik na adres [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) obiekt zawierający mapy generyczny słownik. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z architekturą .NET Native.  
  
 Mapa zawiera dwie sekcje najwyższego poziomu:  
  
-   A [katalogu](#Directory) zawierający względnych adresów wirtualnych (RVA) słowników wszystkie zawarte w tej mapie.  
  
-   -Bajtami [sterty](#Heap) zawierający informacje dotyczące tworzenia wystąpienia obiektu. Rozpoczyna się natychmiast po ostatni wpis katalogu.  
  
<a name="Directory"></a>   
## <a name="the-directory"></a>Katalog  
 Każdy wpis w katalogu, który odwołuje się do przesunięcia wewnątrz sterty; oznacza to, że jest przesunięcie względem początku sterty. Wartość poszczególne wpisy nie jest zawsze unikatowa. istnieje możliwość dla wielu wpisów w katalogu wskaż samo przesunięcie w stosie.  
  
 Część katalogu mapy generyczny słownik ma następującą strukturę:  
  
-   Pierwsze 4 bajty zawiera liczbę pozycji słownika (oznacza to, że liczba względnych adresów wirtualnych w słowniku). Firma Microsoft będzie odnosił się do tej wartości jako *N*. Jeśli ustawiono bit wysokiej, wpisy są sortowane według względny adres wirtualny, w kolejności rosnącej.  
  
-   *N* postępuj zgodnie z wpisy w katalogu. Każdy wpis składa się z 8 bajtów w dwa segmenty 4-bajtowych:  
  
    -   Bajty 0 – 3: ADRES RVA; względny adres wirtualny słownika.  
  
    -   Bajty 4 – 7: Przesunięcie; przesunięcie względem początku sterty.  
  
<a name="Heap"></a>   
## <a name="the-heap"></a>Sterty  
 Rozmiar sterty, może zostać obliczony przez czytnik strumienia poprzez odjęcie długość strumienia od rozmiaru katalogu + 4. Innymi słowy:  
  
```  
Heap Size = Stream.Length – (Directory Size + 4)  
```  
  
 gdzie jest rozmiar katalogu `N * 8`.  
  
 Format dla każdego elementu informacji podczas tworzenia wystąpienia na stosie jest następujący:  
  
-   Długość tego elementu informacji podczas tworzenia wystąpienia w bajtach Format skompresowanych metadanych ECMA. Wartość nie obejmuje to informacje o długości.  
  
-   Liczba typów ogólnych podczas tworzenia wystąpienia lub *T*, format skompresowanych metadanych ECMA.  
  
-   *T* typów, w każdym reprezentowane w formacie podpisu typu ECMA.  
  
 Włączenie długość dla każdego elementu sterty umożliwia proste sortowanie sekcji katalogu bez wywierania wpływu na stosie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebugSymbolProvider2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
