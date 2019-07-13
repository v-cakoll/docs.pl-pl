---
ms.openlocfilehash: d3c6818861f8b0261a9a71a4654029143d928d08
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67856933"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a>Zezwalaj na Unicode na identyfikatory URI, które przypominają udziały UNC

|   |   |
|---|---|
|Szczegóły|W <xref:System.Uri?displayProperty=fullName>, tworząc plik identyfikatorem URI zawierającym zarówno UNC nazwa udziału i już nie spowoduje znaki Unicode w identyfikatorze URI przy użyciu nieprawidłowy stan wewnętrzny. Spowoduje to zmianę działania tylko wtedy, gdy wszystkie następujące elementy są spełnione:<ul><li>Identyfikator URI ma schemat <code>file:</code> i następuje cztery lub więcej ukośników.</li><li>Nazwa hosta rozpoczyna się od znaku podkreślenia ani innych niezarezerwowane symboli.</li><li>Identyfikator URI zawiera znaki Unicode.</li></ul>|
|Sugestia|Aplikacje Praca z identyfikatorów URI spójnie zawierający Unicode mogą mieć wielkiego użyte to zachowanie zabrania odwołania się z udziałami UNC. Te aplikacje powinny używać <xref:System.Uri.IsUnc> zamiast tego.|
|Scope|Krawędź|
|Wersja|4.7.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|

