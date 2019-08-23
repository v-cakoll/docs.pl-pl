---
title: 'Instrukcje: Rejestrowanie podstawowych zestawów międzyoperacyjnych'
ms.date: 03/30/2017
helpviewer_keywords:
- registering primary interop assemblies
- primary interop assemblies, registering
ms.assetid: 4b2fcf8a-429d-43ce-8334-e026040be8bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e61ae55673cbf745ea4c637c5206efe41d8ab276
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946676"
---
# <a name="how-to-register-primary-interop-assemblies"></a>Instrukcje: Rejestrowanie podstawowych zestawów międzyoperacyjnych

Klasy mogą być organizowane tylko przez międzyoperacyjność modelu COM i są zawsze organizowane jako interfejsy. W niektórych przypadkach interfejs używany do organizowania klasy jest nazywany interfejsem klasy. Aby uzyskać informacje na temat przesłaniania interfejsu klasy przy użyciu wybranego interfejsu, zobacz Wywoływanie [otoki com](../../standard/native-interop/com-callable-wrapper.md).

 Chociaż wszyscy deweloperzy, którzy chcą korzystać z typów COM z aplikacji .NET Framework mogą generować zestaw międzyoperacyjny, spowoduje to utworzenie problemu. Za każdym razem, gdy deweloper importuje i podpisuje bibliotekę typów modelu COM, ten deweloper tworzy zestaw unikatowych typów, które są niezgodne z tymi importowanymi i podpisanymi przez innego dewelopera. Rozwiązanie tego problemu niezgodności w przypadku tego typu jest przeznaczone dla każdego dewelopera, aby uzyskać określony przez dostawcę i podpisany podstawowy zestaw międzyoperacyjny.

 Jeśli planujesz uwidocznienie typów COM innych firm w innych aplikacjach, zawsze używaj podstawowego zestawu międzyoperacyjnego dostarczonego przez tego samego wydawcę, który definiuje biblioteka typów. Oprócz zapewnienia gwarantowanej zgodności typów, podstawowe zestawy międzyoperacyjności są często dostosowywane przez dostawcę w celu poprawienia współdziałania.

 Nawet jeśli nie planujesz udostępniania typów COM innych firm, użycie podstawowego zestawu międzyoperacyjnego może ułatwić zadanie współdziałania ze składnikami modelu COM. Jednak ta strategia nie zapewnia żadnych izolacji od zmian, które dostawca może wprowadzać do typów zdefiniowanych w podstawowym zestawie międzyoperacyjnym. Gdy aplikacja wymaga takiej izolacji, wygeneruj własny zestaw międzyoperacyjny zamiast korzystać z podstawowego zestawu międzyoperacyjnego.

 Aby można było odwoływać się do nich za pomocą programu Visual Studio, należy zarejestrować wszystkie nabyte podstawowe zestawy międzyoperacyjności na komputerze deweloperskim. Program Visual Studio szuka i używa podstawowego zestawu międzyoperacyjnego podczas pierwszego odwoływania się do typu z biblioteki typów COM. Jeśli program Visual Studio nie może zlokalizować podstawowego zestawu międzyoperacyjnego skojarzonego z biblioteką typów, zostanie wyświetlony komunikat z prośbą o pozyskanie lub ofertę utworzenia zestawu międzyoperacyjnego. Analogicznie, [Importer biblioteki typów (Tlbimp. exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) używa również rejestru do lokalizowania podstawowych zestawów międzyoperacyjnych.

 Mimo że nie jest konieczne rejestrowanie podstawowych zestawów międzyoperacyjnych, chyba że zamierzasz korzystać z programu Visual Studio, rejestracja oferuje dwie korzyści:

- Zarejestrowany podstawowy zestaw międzyoperacyjny jest jasno oznaczony kluczem rejestru oryginalnej biblioteki typów. Rejestracja jest najlepszym sposobem lokalizowania podstawowego zestawu międzyoperacyjnego na komputerze.

- Można uniknąć przypadkowego generowania i używania nowego zestawu międzyoperacyjnego, jeśli w danym momencie w przyszłości używasz programu Visual Studio do odwoływania się do typu, dla którego masz niezarejestrowany podstawowy zestaw międzyoperacyjny.

Użyj [narzędzia rejestracji zestawu (Regasm. exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) do zarejestrowania podstawowego zestawu międzyoperacyjnego.

## <a name="to-register-a-primary-interop-assembly"></a>Aby zarejestrować podstawowy zestaw międzyoperacyjny

1. W wierszu polecenia wpisz polecenie:

     **Regasm** *AssemblyName*

     W tym poleceniu *AssemblyName* jest nazwą pliku zestawu, który jest zarejestrowany. Regasm. exe dodaje wpis dla podstawowego zestawu międzyoperacyjnego w tym samym kluczu rejestru co oryginalna biblioteka typów.

## <a name="example"></a>Przykład
 Poniższy przykład rejestruje `CompanyA.UtilLib.dll` podstawowy zestaw międzyoperacyjny.

```console
regasm CompanyA.UtilLib.dll
```

## <a name="see-also"></a>Zobacz także

- [Programowanie przy użyciu podstawowych zestawów międzyoperacyjnych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/baxfadst(v=vs.100))
- [Lokalizowanie podstawowych zestawów międzyoperacyjnych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/y06sxw56(v=vs.100))
- [Redystrybuowanie podstawowych zestawów międzyoperacyjnych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w0dt2w20(v=vs.100))
