---
ms.openlocfilehash: d4f0095bc9fde98087dce528c8154d9c9ac6ddb7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621839"
---
### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a>Sprawdzanie pisowni WPF kończy się niepowodzeniem na nieoczekiwany sposób

#### <a name="details"></a>Szczegóły

Obejmuje to wiele problemów z modułem sprawdzania pisowni WPF:<ul><li>Moduł sprawdzania pisowni WPF czasami zgłasza<xref:System.Runtime.InteropServices.COMException?displayProperty=fullName></li><li>Sprawdzanie pisowni WPF kończy się niepowodzeniem, <xref:System.UnauthorizedAccessException> gdy aplikacje są uruchamiane za pomocą polecenia "Uruchom jako inny użytkownik"</li><li>Moduł sprawdzania pisowni WPF nieprawidłowo identyfikuje błędy pisowni w wyrazach złożonych, takich jak "Hausnummer" w języku niemieckim.</li></ul>

#### <a name="suggestion"></a>Sugestia

Problem #1 — ten problem został rozwiązany w programie .NET Framework 4.6.2 #2 — funkcja sprawdzania pisowni WPF nie jest już obsługiwana, gdy aplikacje są uruchamiane za pomocą polecenia "Uruchom jako inny użytkownik". Uruchamianie .NET Framework 4.6.2, aplikacje uruchomione w ten sposób nie przestaną działać w sposób nieoczekiwany — zamiast tego sprawdzanie pisowni zostanie wyłączone w trybie dyskretnym. #3 problemu — ten problem został rozwiązany w .NET Framework 4.6.2.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.6.1|
|Typ|Środowisko uruchomieniowe|
