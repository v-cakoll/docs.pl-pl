---
title: PutInstanceWmi — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja PutInstanceWmi tworzy lub aktualizuje wystąpienie istniejącej klasy.
ms.date: 11/06/2017
api_name:
- PutInstanceWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutInstanceWmi
helpviewer_keywords:
- PutInstanceWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: b33f31d69c64ce520580c29f1014c058c78d0953
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127355"
---
# <a name="putinstancewmi-function"></a>PutInstanceWmi, funkcja

Tworzy lub aktualizuje wystąpienie istniejącej klasy. Wystąpienie jest zapisywane w repozytorium WMI.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a>Parametry

`pInst`\
podczas Wskaźnik do wystąpienia do zapisania.

`lFlags`\
podczas Kombinacja flag mających wpływ na zachowanie tej funkcji. Poniższe wartości są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Jeśli ta wartość jest ustawiona, usługa WMI nie przechowuje żadnych kwalifikatorów z **zmienionym** elementem. <br> Jeśli nie zostanie ustawiona, zakłada się, że ten obiekt nie jest zlokalizowany i wszystkie kwalifikatory są przechowywane z tym wystąpieniem. |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | Utwórz wystąpienie, jeśli nie istnieje, lub zastąp je, jeśli już istnieje. |
| `WBEM_FLAG_UPDATE_ONLY` | 1 | Zaktualizuj wystąpienie. Wystąpienie musi istnieć, aby wywołanie zakończyło się pomyślnie. |
| `WBEM_FLAG_CREATE_ONLY` | 2 | Utwórz wystąpienie. Wywołanie zakończy się niepowodzeniem, jeśli wystąpienie już istnieje. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Flaga powoduje wywołanie półsynchronicznej. |

`pCtx`\
podczas Zazwyczaj ta wartość jest `null`. W przeciwnym razie jest wskaźnikiem do wystąpienia [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , które może być używane przez dostawcę dostarczającego żądane klasy.

`ppCallResult`\
określoną Jeśli `null`, ten parametr jest nieużywany. Jeśli `lFlags` zawiera `WBEM_FLAG_RETURN_IMMEDIATELY`, funkcja wraca bezpośrednio z `WBEM_S_NO_ERROR`. Parametr `ppCallResult` odbiera wskaźnik do nowego obiektu [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) .

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Użytkownik nie ma uprawnienia do aktualizowania wystąpienia określonej klasy. |
| `WBEM_E_FAILED` | 0x80041001 | Wystąpił nieokreślony błąd. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | Klasa obsługująca to wystąpienie jest nieprawidłowa. |
| `WBEM_E_ILLEGAL_NULL` | 0x80041028 | `null` określono dla właściwości, której nie można `null`, takiej jak taka, która jest oznaczona przez kwalifikator **Indexed** lub **NOT_NULL** . |
| `WBEM_E_INVALID_OBJECT` | 0x8004100f | Określone wystąpienie jest nieprawidłowe. (Na przykład wywoływanie `PutInstanceWmi` z klasą zwraca tę wartość). |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | Określono flagę `WBEM_FLAG_CREATE_ONLY`, ale wystąpienie już istnieje. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY` określono w `lFlags`, ale wystąpienie nie istnieje. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało dostępnej pamięci, aby ukończyć tę operację. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | Usługa WMI prawdopodobnie została zatrzymana i ponownie uruchomiona. Ponownie wywołaj [ConnectServerWmi](connectserverwmi.md) . |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Łącze zdalnego wywołania procedury (RPC) między bieżącym procesem a usługą WMI nie powiodło się. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie. |

## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IWbemServices::P utinstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) .

Funkcja `PutInstanceWmi` obsługuje tworzenie wystąpień i aktualizowanie wystąpień istniejących klas.  W zależności od sposobu ustawienia parametru `pCtx`, niektóre lub wszystkie właściwości wystąpienia są aktualizowane.

Gdy wystąpienie wskazywane przez `pInst` należy do podklasy, system Windows Management wywoła wszystkich dostawców odpowiedzialnych za klasy, z których dziedziczy Klasa. Aby oryginalne żądanie `PutInstanceWmi` powiodło się, wszyscy dostawcy muszą pomyślnie wykonać odpowiednie działania. Dostawca obsługujący klasę najwyższego poziomu w hierarchii jest nazywany pierwszym. Kolejność wywoływania jest kontynuowana z podklasą klasy najwyższej i przechodzi od góry do dołu, dopóki zarządzanie systemem Windows osiągnie dostawcę dla klasy będącej właścicielem wystąpienia wskazywanym przez `pInst`.
Zarządzanie systemem Windows nie wywołuje dostawców dla żadnej z klas podrzędnych wystąpienia.

Gdy aplikacja musi zaktualizować wystąpienie należące do hierarchii klas, parametr `pInst` musi wskazywać na wystąpienie zawierające właściwości do zmodyfikowania. Oznacza to, że należy rozważyć wystąpienie docelowe, które należy do **ClassB**. Wystąpienie **ClassB** dziedziczy z **ClassA**, a **ClassA** definiuje Właściwość **propa**. Jeśli aplikacja chce wprowadzić zmianę wartości **propa** w wystąpieniu **ClassB** , musi ustawić `pInst` na to wystąpienie, a nie wystąpienie elementu **ClassA**.

Wywoływanie `PutInstanceWmi` na wystąpieniu klasy abstrakcyjnej jest niedozwolone.

Jeśli wywołanie funkcji nie powiedzie się, można uzyskać dodatkowe informacje o błędzie, wywołując funkcję [GetErrorInfo](geterrorinfo.md) .

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówek:** WMINet_Utils. idl

**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
