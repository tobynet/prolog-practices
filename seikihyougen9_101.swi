% http://swish.swi-prolog.org/p/TzBGzkkC.pl
%
% via http://nojiriko.asia/prolog/seikihyogen9_101.html
%
% 出典::正規表現 Part9 #101
% http://toro.2ch.net/test/read.cgi/tech/1323566370/101
%
% > ●正規表現の使用環境
% > C#
% >
% > ●検索か置換か？
% > 置換
% >
% > ●説明
% > 文字列の先頭の部分のカッコを消したい
% >
% > ●対象データ
% > (hoge)あいうえお
% >
% > ●希望する結果
% > hogeあいうえお


%  試す場合:
%  
%  ?- 文字列置換('(あなたとジャバ),(今すぐ)ダウンロード', X).
%  
%  や
%  
%  ?- main.
%  
%  などとする。


文字列置換(Input, X) :- 
    atom_chars(Input, List),
    文字列置換(List, [], Result),
    atomic_list_concat(Result, X).

    %writef('%t => %t', [Input, X]), nl.
    % swish では "No permission to call sandboxed" とのこと。

% 末尾再帰用の述語定義
文字列置換([], X, X).
文字列置換([Head|Tail], X, [ReplacedHead|Result]) :-
    置換(Head, ReplacedHead),
    文字列置換(Tail, X, Result).

置換('(', '') :- !.
置換(')', '') :- !.
置換(X, X).

main :-
    文字列置換(
        'あなたとジャバ,今すぐダウンロード',
        'あなたとジャバ,今すぐダウンロード'),

    文字列置換(
        '(あなたとジャバ),今すぐダウンロード',
        'あなたとジャバ,今すぐダウンロード'),

    文字列置換(
        'あなたとジャバ,(今すぐ)ダウンロード',
        'あなたとジャバ,(今すぐ)ダウンロード')

    ; writeln('置換失敗!!').

% 先頭部分のカッコを消す(_元, _結果) :-
%     先頭部分のカッコを消す(_元, _結果, []).
%
% 先頭部分のカッコを消す(_元, _結果, []).
% 先頭部分のカッコを消す(_元, _結果, [_先頭|_残り]) :-
%     append(_先頭, _残り, _結果),
%     先頭部分のカッコを消す(_元, _残り).
%
% main :-
%     _対象 = '(hoge)あいうえお',
%     先頭部分のカッコを消す(_対象, _結果),
%     writeln(_結果).

% swish 用にコメントアウト
%:- main.
%:- main, halt.
