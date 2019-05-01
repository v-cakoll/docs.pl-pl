---
title: Plik określony w nazwie pliku nie jest prawidłowym plikiem XML
ms.date: 07/20/2015
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
ms.openlocfilehash: 89499b07e767bd0b3a777db4e5155f64a4357f0c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052316"
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a>Plik określony w nazwie pliku nie jest prawidłowym plikiem XML

Podanej nazwy pliku nie jest prawidłowym plikiem XML. Aby określić dozwolone struktury i zawartości dokumentu XML, można użyć definicji typu dokumentu (DTD), schemat Microsoft-danych XML (XDR) lub schematu języka (XSD) definicji schematu XML. Schematy XSD są preferowanym sposobem określenia gramatyki XML w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].

> [!NOTE]
> W niektórych starszych wersjach programu Visual Studio **Projektant XML** jest Projektant typizowanych zestawów danych i schematu XML. **Projektant XML** nadal można tworzyć i edytować pliki schematów XML. W programie Visual Studio 2012 designer do tworzenia i edytowania zestawów jest jednak **Projektanta obiektów Dataset**. Aby uzyskać więcej informacji, zobacz [tworzenie i edytowanie wpisanych zestawów danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120)).

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Sprawdź, czy są podawania poprawnej nazwy pliku.

- Sprawdź, czy określony plik zawiera prawidłowy kod XML, ładując plik XML, który chcesz zaewidencjonować w **Projektant XML**. Z **XML** menu, kliknij przycisk **sprawdzania poprawności XML**. Błędy są wyświetlane w **listy zadań**.

- Jeśli plik XML ma skojarzonego schematu XML, sprawdź, czy elementy są wyświetlane w zdefiniowanej strukturze i że zawartość poszczególnych elementów zgodne typy danych zadeklarowany, określona w schemacie.

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml>
- [Instrukcje: Analizowanie ścieżek pliku](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)