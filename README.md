## Exemplo Aula Debug - Identifique os Debugs

import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class DebugExemplo {

    public static void main(String[] args) {

        System.out.println("=========================================================");
        System.out.println("Exemplo do calculo do retangulo com funções");
        System.out.println("=========================================================");

        calcularSomaAreas();

        System.out.println("=========================================================");
        System.out.println("Exemplo de mostrar lista de números com funções");
        System.out.println("=========================================================");

        mostrarTodosOsValoresListaNumero(retornarListaNumeros());

        System.out.println("=========================================================");
        List<Integer> listaNumerosArray = retornarListaNumeros();
        mostrarTodosOsValoresListaNumero(listaNumerosArray);

        List<String> listaNomesComQuantidade = mostrarNomesComPosicao(retornarListaNumeros());
        System.out.println("=========================================================");
        System.out.println("Exemplo de mostrar lista de quantidade de nomes com funções");
        System.out.println("=========================================================");
        System.out.println("Exemplo de array = $listaNomesComQuantidade");
        
    }

    public static void calcularSomaAreas() {
        //Exemplo de uso do retorno de outra função
        double somaAreas = calcularAreaRetanguloComInputUsuario() + calcularAreaRetangulo(2.0, 4.0);
        System.out.println("A area total de construção é de " + somaAreas);
    }

    public static double calcularAreaRetanguloComInputUsuario() {
        Scanner ler = new Scanner(System.in);

        System.out.println("Digite a base: ");
        double base = ler.nextDouble();

        System.out.println("Digite a altura: ");
        double altura = ler.nextDouble();

        double areaRetangulo = base * altura;
        System.out.println("O valor da área é de " +areaRetangulo);

        return areaRetangulo;
    }

    public static double calcularAreaRetangulo(double base, double altura) {
        double areaRetangulo = base * altura;
        System.out.println("O valor da área do retangulo é " + areaRetangulo );
        return areaRetangulo;
    }

    public static void mostrarTodosOsValoresListaNumero(List<Integer> numeros) {
        for (int i = 0; i < numeros.size(); i++) {
            System.out.println(numeros.get(i));
        }
    }

    public static List<Integer> retornarListaNumeros() {
        List<Integer>  listaNumero = new ArrayList<>(3);
        return listaNumero;
    }

    public static List<String> mostrarNomesComPosicao(List<Integer> quantidade) {
        List<String> nomesExibir = new ArrayList<>();


        for (int i = 0; i < quantidade.size(); i++) {
            nomesExibir.add(quantidade.get(i) + "nomes");
            System.out.println(nomesExibir.get(i));
        }

        return nomesExibir;
    }

    public static List<String> retornarListaNomes() {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Digite a capacidade: ");
        int capacidade = scanner.nextInt();

        List<String> listaNomes = new ArrayList<>();

        for (int i = 0; i < capacidade; i++) {
            System.out.println("Digite um nome: ");
            listaNomes.add(scanner.nextLine());
        }

        return listaNomes;
    }
}

## Forma que compreende pra desobrir os erros.

1- Na função retornarListaNumeros(), removi o tamanho inicial do ArrayList, pois ele será adicionado posteriormente com o método add().

2- Na função mostrarNomesComPosicao(), o parâmetro foi alterado de List<Integer> quantidadepara List<String> listaNomes.
  
3- Na função retornarListaNomes(), adicionei uma chamada para scanner.nextLine()após a leitura de capacidade, pois o método nextInt()não consome a nova linha.
  
4- No final do código, na impressão da lista de nomes com quantidade, corrigi o trecho "$listaNomesComQuantidade"para " + listaNomesComQuantidade".
