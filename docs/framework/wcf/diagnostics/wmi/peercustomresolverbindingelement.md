---
title: PeerCustomResolverBindingElement
ms.date: 03/30/2017
ms.assetid: 9ccc2770-a20e-4dff-9970-f56ad8aec2b5
ms.openlocfilehash: c7f8fd23133cd83ad87a00134b9755b94f531d8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963062"
---
# <a name="peercustomresolverbindingelement"></a>PeerCustomResolverBindingElement

PeerCustomResolverBindingElement

## <a name="syntax"></a>Składnia

```csharp
class PeerCustomResolverBindingElement : PeerResolverBindingElement
{
    string Address;
    string Binding;
};
```

## <a name="methods"></a>Metody

Klasa elementów PeerCustomResolverBindingElement nie definiuje żadnych metod.

## <a name="properties"></a>Właściwości

 Klasa elementów PeerCustomResolverBindingElement ma następujące właściwości:

### <a name="address"></a>Adres

Typ danych: ciąg

Typ dostępu: tylko do odczytu

Adres niestandardowego elementu równorzędnego programu rozpoznawania nazw.

### <a name="binding"></a>Wiązanie

Typ danych: ciąg

Typ dostępu: tylko do odczytu

Nazwa konfiguracji powiązania.

## <a name="requirements"></a>Wymagania

|MOF|Zadeklarowana w Servicemodel.mof.|
|---------|-----------------------------------|
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.PeerCustomResolverBindingElement>
