// Importação das bibliotecas necessárias
import java.util.Random;
import java.util.Scanner;

// Classe principal do aplicativo
public class Appforca {
    // Declaração de variáveis estáticas que armazenarão informações dos jogadores
    static int[] pontos = new int[3]; // Armazena a pontuação de cada jogador
    static String[] nome = new String[3]; // Armazena o nome de cada jogador
    static int contador = 0; // Contador de acertos
    static char resposta; // Variável para armazenar respostas do usuário

    // Método principal do programa
    public static void main(String[] args) {
        Scanner prompt = new Scanner(System.in);

        // Exibição do menu de opções
        System.out.println("1 - Iniciar o jogo");
        System.out.println("2 - Verificar pontuação máxima");
        System.out.println("3 - Sair");

        // Leitura da escolha do usuário
        int escolha = prompt.nextInt();

        // Estrutura de seleção para a escolha do usuário
        switch (escolha) {
            case 1:
                cruzadinhakkkXD(); // Iniciar o jogo
                break;
            case 2:
                VerificarPontuacao(); // Verificar a pontuação máxima
                break;
            case 3:
                System.out.println("Ok, adeus"); // Encerrar o programa
                break;
            default:
                System.out.println("Opção inválida"); // Mensagem para escolha inválida
        }

        prompt.close(); // Fechar o scanner
    }

    // Método para iniciar o jogo
    public static void cruzadinhakkkXD() {
        Random rand = new Random();
        Scanner prompt = new Scanner(System.in);

        // Inicialização dos nomes dos jogadores
        for (int i = 0; i < nome.length; i++) {
            nome[i] = null;
        }

        // Solicitação do nome do jogador
        for (int i = 0; i < 1; i++) {
            System.out.println("\nDigite seu nome para aparecer no jogo: ");
            nome[i] = prompt.nextLine();
        }

        // Configuração do jogo de adivinhação de palavras
        System.out.println("Acerte a palavra correta");
        String[] palavrasecreta = {  "JAVA", "PYTHON", "CPLUSPLUS", "JAVASCRIPT", "RUBY", "PHP", "ROGERMALUCO" };
        boolean palavravalida = false;
        StringBuilder palavraatual = new StringBuilder();
        int tentativas = 0;
        String palavraescolhida = palavrasecreta[rand.nextInt(palavrasecreta.length)];

        // Inicialização da palavra atual com "_"
        for (int i = 0; i < palavraescolhida.length(); i++) {
            palavraatual.append("_");
        }

        // Apresentação inicial do jogo
        System.out.printf("Você tem 5 tentativas para acertar.\nPalavra atual: %s\n", palavraatual);

        // Loop para adivinhação da palavra
        while (!palavravalida) {
            System.out.print("Digite uma letra: ");
            boolean LetraVerdadeiro = false;
            String letra = prompt.next();
            char letrachar = letra.charAt(0);

            // Loop para verificar se a letra está na palavra
            for (int i = 0; i < palavraescolhida.length(); i++) {
                if (palavraescolhida.charAt(i) == letrachar) {
                    LetraVerdadeiro = true;
                    palavraatual.setCharAt(i, letrachar);
                }
            }

            // Verificações adicionais para validade da entrada
            if (letra.length() > 1) {
                System.out.println("Digita só uma letra Animal");
                tentativas = tentativas + 1;
            }
            if (!Character.isLetter(letrachar)) {
                System.out.print("Tu só pode digitar letra seu Acefalo");
            }

            // Exibição da palavra atualizada e feedback ao jogador
            System.out.printf("Palavra atual: %s\n", palavraatual);

            if (LetraVerdadeiro) {
                System.out.println("Letra correta!");
            } else {
                tentativas = tentativas + 1;
                System.out.println("Letra incorreta!");
            }

            // Verificação de tentativas esgotadas
            if (tentativas == 5) {
                System.out.println("Você perdeu TROUXA!");
                palavravalida = true;

                // Exibição da pontuação e opções para continuar ou sair
                System.out.println("\nSua pontuação:");
                System.out.println("Continuar jogando a forca maldita?");
                System.out.println("1 - Sim");
                System.out.println("2 - Não");
                int escolha2 = prompt.nextInt();
                switch (escolha2) {
                    case 1:
                        cruzadinhakkkXD(); // Reiniciar o jogo
                        break;
                    case 2:
                        System.out.println("Ok, adeus"); // Encerrar o programa
                        break;
                    default:
                        System.out.println("Opção inválida"); // Mensagem para escolha inválida
                }
            }

            // Verificação de acerto da palavra
            if (palavraatual.toString().equals(palavraescolhida)) {
                System.out.println("\033[H\033[2J");
                System.out.printf("\nParabéns, você acertou a palavra: [%s]. ", palavraescolhida);
                palavravalida = true;
                contador = contador + 1;

                // Atualização da pontuação do jogador
                if (contador == 1) {
                    pontos[0] = pontos[0] + 1;
                }

                // Exibição da pontuação do jogador
                System.out.printf("\nPontuação do jogador %s: %d\n", nome[0], pontos[0]);
                System.out.printf("\n%s, você deseja jogar novamente? (S/N): ", nome[0]);

                // Leitura da resposta do jogador para continuar ou sair
                char resposta = prompt.next().charAt(0);
                if (resposta == 'S' || resposta == 's') {
                    cruzadinhakkkXD(); // Reiniciar o jogo
                }
                if (resposta == 'N' || resposta == 'n') {
                    main(palavrasecreta); // Voltar ao menu principal
                    palavravalida = true;
                    break;
                }

                contador = contador + 1;

                break;
            }
        }
        prompt.close(); // Fechar o scanner
    }

    // Método para verificar a pontuação
    public static String VerificarPontuacao() {
        Scanner prompt = new Scanner(System.in);
        System.out.println("\033[H\033[2J");
        boolean palavraValida = false;

        while (!palavraValida) {
            // Verificação se o jogador jogou ou acertou alguma palavra
            if (contador == 0 || nome[0] == null) {
                palavraValida = true;
                System.out.println("Você ainda não jogou ou não acertou nenhuma palavra!");
                System.out.println("Voltar para o menu?");
                System.out.println("1 - Sim");
                System.out.println("2 - Não");
                int escolha2 = prompt.nextInt();
                switch (escolha2) {
                    case 1:
                        main(nome); // Voltar ao menu principal
                        break;
                    case 2:
                        System.out.println("Ok, Tchau"); // Encerrar o programa
                        Sair();
                        break;
                    default:
                        System.out.println("Opção inválida"); // Mensagem para escolha inválida
                }
            }

            // Exibição da pontuação dos jogadores
            if (nome[0] != null) {
                for (int i = 0; i < nome.length; i++) {
                    System.out.printf("\nPontuação do jogador %s: %d.\n", nome[i], pontos[i]);
                }

                // Opções para continuar ou sair
                System.out.printf("\n%s, você deseja voltar para o menu? (S/N): ", nome[0]);
                char resposta = prompt.next().charAt(0);
                if (resposta == 'S' || resposta == 's') {
                    main(nome); // Voltar ao menu principal
                }
                if (resposta == 'N' || resposta == 'n') {
                    Sair(); // Encerrar o programa
                    palavraValida = true;
                    break;
                }
                palavraValida = true;
            }

            if (resposta == 'N' || resposta == 'n') {
                Sair(); // Encerrar o programa
                palavraValida = true;
                break;
            }
        }
        prompt.close(); // Fechar o scanner
        return "VerificarPontuacao";
    }

    // Método para encerrar o jogo
    public static String Sair() {
        System.out.println("\033[H\033[2J");
        System.out.println("Jogo encerrado.");
        return "Jogo encerrado";
    }
}