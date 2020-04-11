---
title: 'Porady: tworzenie otok COM'
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
ms.openlocfilehash: 035d6439ec90426d7b68e05043ea8b6722f81d28
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121598"
---
# <a name="how-to-create-com-wrappers"></a>Porady: tworzenie otok COM

Otoki modelu com (Component Object Model) można tworzyć przy użyciu funkcji programu Visual Studio 2005 lub narzędzi .NET Framework Tlbimp.exe i Regasm.exe. Obie metody generują dwa typy otoki COM:

- [Otoka wywołalna w czasie wykonywania](../../standard/native-interop/runtime-callable-wrapper.md) z biblioteki typów do uruchomienia obiektu COM w kodzie zarządzanym.

- Otoka [rozpisywalna com](../../standard/native-interop/com-callable-wrapper.md) z wymaganymi ustawieniami rejestru do uruchomienia obiektu zarządzanego w aplikacji macierzystej.

W programie Visual Studio 2005 można dodać otoki COM jako odwołanie do projektu.

## <a name="wrap-com-objects-in-a-managed-application"></a>Zawijanie obiektów COM w aplikacji zarządzanej

### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a>Aby utworzyć otokę wywoływaną w czasie wykonywania przy użyciu programu Visual Studio

1. Otwórz projekt dla aplikacji zarządzanej.

2. W menu **Projekt** kliknij polecenie **Pokaż wszystkie pliki**.

3. W menu **Projekt** kliknij polecenie **Dodaj odwołanie**.

4. W oknie dialogowym Dodawanie odwołania kliknij kartę **COM,** wybierz składnik, którego chcesz użyć, a następnie kliknij przycisk **OK**.

     W **Eksploratorze rozwiązań**należy zauważyć, że składnik COM jest dodawany do folderu Odwołania w projekcie.

Teraz można napisać kod, aby uzyskać dostęp do obiektu COM. Można rozpocząć od deklarowania obiektu, na `Imports` przykład z instrukcją dla języka Visual Basic lub instrukcją `Using` dla języka C#.

> [!NOTE]
> Jeśli chcesz zaprogramować składniki pakietu Microsoft Office, najpierw zainstaluj [redystrybucyjne zestawy interpli pakietu Microsoft Office.](https://www.microsoft.com/Download/details.aspx?id=3508)
  
### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a>Aby utworzyć otokę wywoływaną w czasie wykonywania przy użyciu narzędzi .NET Framework  
  
- Uruchom narzędzie [Tlbimp.exe (Importer biblioteki typów).](../tools/tlbimp-exe-type-library-importer.md)  
  
 To narzędzie tworzy zestaw zawierający metadane w czasie wykonywania dla typów zdefiniowanych w oryginalnej bibliotece typów.  
  
## <a name="wrap-managed-objects-in-a-native-application"></a>Zawijanie obiektów zarządzanych w aplikacji macierzystej  
  
### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a>Aby utworzyć otokę wywoływaną przez COM przy użyciu programu Visual Studio  
  
1. Utwórz projekt biblioteki klas dla klasy zarządzanej, którą chcesz uruchomić w kodzie macierzystym. Klasa musi mieć konstruktora bez parametrów.  
  
     Sprawdź, czy masz pełny czteroczęściowy numer wersji dla złożenia w pliku AssemblyInfo. Ten numer jest wymagany do obsługi przechowywania wersji w rejestrze systemu Windows. Aby uzyskać więcej informacji na temat numerów wersji, zobacz [Przechowywanie wersji zestawu](../../standard/assembly/versioning.md).  
  
2. W menu **Projekt** kliknij polecenie **Właściwości**.  
  
3. Kliknij kartę **Kompilowanie.**  
  
4. Zaznacz pole wyboru **Zarejestruj się dla współdziałania COM.**  
  
 Podczas tworzenia projektu, zestaw jest automatycznie rejestrowany dla com interop. Jeśli budujesz aplikację natywną w programie Visual Studio 2005, można użyć zestawu, klikając **dodaj odwołanie** w menu **projektu.**  
  
### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a>Aby utworzyć otokę wywoływaną przez COM przy użyciu narzędzi .NET Framework  
  
Uruchom narzędzie [Regasm.exe (narzędzie rejestracji zestawu).](../tools/regasm-exe-assembly-registration-tool.md)  
  
To narzędzie odczytuje metadane zestawu i dodaje niezbędne wpisy do rejestru. W rezultacie klienci COM mogą tworzyć klasy .NET Framework w sposób przejrzysty. Można użyć zestawu tak, jakby był natywną klasą COM.  
  
Program Regasm.exe można uruchomić w zestawie znajdującym się w dowolnym katalogu, a następnie uruchomić [plik Gacutil.exe (Narzędzie globalnej pamięci podręcznej zestawów),](../tools/gacutil-exe-gac-tool.md) aby przenieść go do globalnej pamięci podręcznej zestawów. Przenoszenie zestawu nie unieważnia wpisów rejestru lokalizacji, ponieważ globalna pamięć podręczna zestawów jest zawsze sprawdzana, jeśli zestaw nie zostanie znaleziony gdzie indziej.  
  
## <a name="see-also"></a>Zobacz też

- [Wywoływana otoka środowiska uruchomieniowego](../../standard/native-interop/runtime-callable-wrapper.md)
- [Wywoływana otoka COM](../../standard/native-interop/com-callable-wrapper.md)
