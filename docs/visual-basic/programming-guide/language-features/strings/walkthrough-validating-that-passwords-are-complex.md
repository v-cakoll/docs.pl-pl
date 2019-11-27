---
title: Walidacja złożoności haseł
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: 6e8697379a6fbb5cc15b60291e5b822897c2c013
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348329"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a>Wskazówki: sprawdzanie poprawności złożoności haseł (Visual Basic)
Ta metoda sprawdza pewne cechy silnego hasła i aktualizuje parametr ciągu z informacjami o tym, które sprawdzenia nie powiodło się.  
  
 Hasła mogą być używane w zabezpieczonym systemie w celu autoryzowania użytkownika. Jednak hasła muszą być trudne dla nieautoryzowanych użytkowników. Osoby atakujące mogą korzystać z programu *ataku słownikowego* , który wykonuje iterację we wszystkich słowach w słowniku (lub wielu słownikach w różnych językach) i sprawdza, czy którykolwiek z tych słów działa jako hasło użytkownika. Słabe hasła, takie jak "Yankees" lub "Mustang", można szybko wypróbować. Silniejsze hasła, na przykład "? "L1N3vaFiNdMeyeP@sSWerd!", są znacznie mniej znaczące do odgadnięcia. System chroniony hasłem powinien mieć pewność, że użytkownicy wybierają silne hasła.  
  
 Silne hasło jest złożone (zawierające kombinację wielkich, małych liter, cyfr i znaków specjalnych) i nie jest słowem. W tym przykładzie pokazano, jak sprawdzić złożoność.  
  
## <a name="example"></a>Przykład  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbcnRegEx#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Wywołaj tę metodę, przekazując ciąg, który zawiera to hasło.  
  
 Ten przykład wymaga:  
  
- Dostęp do elementów członkowskich <xref:System.Text.RegularExpressions> przestrzeni nazw. Dodaj instrukcję `Imports`, jeśli nie masz w pełni kwalifikowanej nazwy elementu członkowskiego w kodzie. Aby uzyskać więcej informacji, zobacz [Imports — Instrukcja (przestrzeń nazw i typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="security"></a>Bezpieczeństwo  
 Jeśli przenosisz hasło za pośrednictwem sieci, musisz użyć bezpiecznej metody przesyłania danych. Aby uzyskać więcej informacji, zobacz [ASP.NET zabezpieczenia aplikacji sieci Web](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100)).
  
 Dokładność funkcji `ValidatePassword` można poprawić, dodając dodatkowe sprawdzenia złożoności:  
  
- Porównaj hasło i jego podciągi w odniesieniu do nazwy użytkownika, identyfikatora użytkownika i słownika zdefiniowanego przez aplikację. Ponadto Traktuj podobne wizualnie znaki jako równoważne podczas przeprowadzania porównania. Na przykład Traktuj litery "l" i "e" jako równoważne cyfrom "1" i "3".  
  
- Jeśli istnieje tylko jeden znak pisany wielkimi literami, upewnij się, że nie jest on pierwszym znakiem hasła.  
  
- Upewnij się, że ostatnie dwa znaki hasła są literami znaków.  
  
- Nie Zezwalaj na hasła, w których wszystkie symbole są wprowadzane z górnego wiersza klawiatury.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Text.RegularExpressions.Regex>
- [Zabezpieczenia aplikacji sieci Web ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))
