---
title: Plik określony w nazwie pliku nie jest prawidłowym plikiem XML
ms.date: 07/20/2015
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
ms.openlocfilehash: a84042490935e3e7e5a6de2a802d9effd5b4d3d4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84358351"
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a>Plik określony w nazwie pliku nie jest prawidłowym plikiem XML

Podana nazwa pliku nie jest prawidłowym plikiem XML. Aby określić dozwoloną strukturę i zawartość dokumentu XML, można użyć definicji typu dokumentu (DTD), schematu z ograniczeniami (XDR) języka Microsoft XML lub schematu definicji schematu XML (XSD). Schematy XSD są preferowanym sposobem określania gramatyki XML w .NET Framework.

> [!NOTE]
> W niektórych wcześniejszych wersjach programu Visual Studio **Projektant XML** jest projektantem dla wpisanych zestawów danych i schematu XML. **Projektant XML** może nadal służyć do tworzenia i edytowania plików schematu XML. Jednak w programie Visual Studio 2012 Projektant do tworzenia i edytowania wpisanych zestawów danych jest **Projektant obiektów DataSet**. Aby uzyskać więcej informacji, zobacz [Tworzenie i edytowanie wpisanych zestawów danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120)).

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Sprawdź, czy podano poprawną nazwę pliku.

- Sprawdź, czy określony plik zawiera prawidłowy kod XML przez załadowanie pliku XML, który chcesz zaewidencjonować do **projektanta XML**. W menu **XML** kliknij polecenie **Weryfikuj kod XML**. Błędy są wyświetlane w **Lista zadań**.

- Jeśli plik XML ma skojarzony schemat XML, sprawdź, czy elementy są widoczne w zdefiniowanej strukturze i czy zawartość poszczególnych elementów jest zgodna z zadeklarowanymi typami danych określonymi w schemacie.

## <a name="see-also"></a>Zobacz też

- <xref:System.Xml>
- [Instrukcje: Analizowanie ścieżek plików](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
