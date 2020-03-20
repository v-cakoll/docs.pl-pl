---
title: Zmiany w obszarze nazw System.Uri w wersji 2.0
ms.date: 03/30/2017
ms.assetid: 35883fe9-2d09-4d8b-80ca-cf23a941e459
ms.openlocfilehash: 987010b8367069e8089df3f809d23f258bb68f2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "61642766"
---
# <a name="changes-to-the-systemuri-namespace-in-version-20"></a>Zmiany w obszarze nazw System.Uri w wersji 2.0

Wprowadzono kilka zmian <xref:System.Uri?displayProperty=nameWithType> w klasie. Zmiany te naprawiły nieprawidłowe zachowanie, zwiększoną użyteczność i zwiększone zabezpieczenia.

## <a name="obsolete-and-deprecated-members"></a>Przestarzali i przestarzali członkowie

 Konstruktorów:

- Wszystkie konstruktory, które mają `dontEscape` parametr.

 Metody:

- <xref:System.Uri.CheckSecurity%2A>

- <xref:System.Uri.Escape%2A>

- <xref:System.Uri.Canonicalize%2A>

- <xref:System.Uri.Parse%2A>

- <xref:System.Uri.IsReservedCharacter%2A>

- <xref:System.Uri.IsBadFileSystemCharacter%2A>

- <xref:System.Uri.IsExcludedCharacter%2A>

- <xref:System.Uri.EscapeString%2A>

## <a name="changes"></a>Zmiany

- W przypadku schematów URI, o których wiadomo, że nie mają części kwerendy (plik, ftp i inne), znak '?' jest zawsze zmieniany i nie jest uważany za początek <xref:System.Uri.Query%2A> części.

- W przypadku identyfikatorów URI `c:\directory\file@name.txt`pliku niejawnego (formularza) znak fragmentu ("#") jest <xref:System.Uri.LocalPath%2A> `true`zawsze zmieniany, chyba że wymagane jest pełne unescaping lub jest .

- Usunięto obsługę nazwy hosta UNC; przyjęto specyfikację IDN reprezentującą międzynarodowe nazwy hostów.

- <xref:System.Uri.LocalPath%2A>zawsze zwraca ciąg całkowicie nieograniczony.

- <xref:System.Uri.ToString%2A>nie unescape znak "%", "?", lub "#".

- <xref:System.Uri.Equals%2A>teraz uwzględnia <xref:System.Uri.Query%2A> część kontroli równości.

- Operatory "==" i "!=" są zastępowane i połączone z <xref:System.Uri.Equals%2A> metodą.

- <xref:System.Uri.IsLoopback%2A>teraz daje spójne wyniki.

- Identyfikator URI`file:///path`" " nie `file://path`jest już tłumaczony na .

- "#" jest teraz rozpoznawany jako terminator nazwy hosta. Oznacza to, `http://contoso.com#fragment` że jest `http://contoso.com/#fragment`teraz konwertowany do .

- Naprawiono błąd podczas łączenia podstawowego identyfikatora URI z fragmentem.

- Naprawiono <xref:System.Uri.HostNameType%2A> błąd.

- Naprawiono błąd w analizowaniu NNTP.

- Identyfikator URI formularza HTTP:contoso.com zgłasza teraz wyjątek analizy.

- Framework poprawnie obsługuje userinfo w identyfikatorze URI.

- Kompresja ścieżki identyfikatora URI jest stała, dzięki czemu uszkodzony identyfikator URI nie może przechodzić przez system plików nad katalogiem głównym.

## <a name="see-also"></a>Zobacz też

- <xref:System.Uri?displayProperty=nameWithType>
